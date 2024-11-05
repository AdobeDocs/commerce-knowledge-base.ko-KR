---
title: "캐시 플러시 시 시 배포 실패: '캐시' 네임스페이스에 정의된 명령이 없습니다.' 오류"
description: 이 문서에서는 다음 오류**캐시 네임스페이스에 정의된 명령이 없음**과 함께 배포가 실패하는 경우의 문제에 대한 해결 방법을 제공합니다.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# 캐시 플러시 시 시 배포 실패: &quot;&#39;cache&#39; 네임스페이스에 정의된 명령이 없습니다.&quot; 오류

>[!WARNING]
>
>라이브 프로덕션 사이트에서 이 작업을 수행하는 경우 이러한 단계를 수행하기 전에 먼저 데이터베이스를 백업합니다.

이 문서에서는 배포에 실패하고 로그의 오류 중 하나가 다음과 같은 경우 발생하는 문제에 대한 해결 방법을 제공합니다.

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce 2.4.x

## 문제

<u>재현 단계</u>:

배포를 시도합니다.

<u>예상 결과</u>:

을(를) 배포했습니다.

<u>실제 결과</u>:

을 배포하지 못했습니다. 로그에 다음 *캐시 네임스페이스에 명령이 없습니다*.

### 원인

**`core_config_data`** 테이블에 데이터베이스에 더 이상 존재하지 않는 저장소 ID 또는 웹 사이트 ID에 대한 구성이 포함되어 있습니다. 이 문제는 다른 인스턴스/환경에서 데이터베이스 백업을 가져왔을 때 발생하며, 이러한 범위에 대한 구성은 연결된 저장소/웹 사이트가 삭제되어도 데이터베이스에 남아 있습니다.

### 솔루션

웹 사이트가 한 개만 있는 경우 웹 사이트에 대한 두 번째 테스트는 적용되지 않으며 스토어에 대한 테스트만 수행하면 됩니다.

이 문제를 해결하려면 해당 구성에서 남은 잘못된 행을 식별합니다.

1. 서버에 SSH를 연결하고 이 명령을 실행합니다.

   `bin/magento`

1. 오류 메시지는 삭제된 사이트에서 데이터베이스에 남아 있는 행 및 테이블을 나타낼 수 있습니다. 예를 들어 요청된 저장소를 찾을 수 없음을 나타내는 오류가 다음과 같습니다.

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. 이 [!DNL MySQL] 쿼리를 실행하여 스토어를 찾을 수 없는지 확인합니다. 이 값은 2단계에서 오류 메시지로 표시됩니다.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 다음 [!DNL MySQL] 문을 실행하여 잘못된 행을 삭제합니다.

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 이 명령 다시 실행:

   `bin/magento`

   요청한 ID X의 웹 사이트를 찾을 수 없음을 나타내는 아래와 같은 오류가 발생하는 경우 나머지 구성이 있습니다        삭제된 스토어와 웹 사이트의 데이터베이스.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   이 [!DNL MySQL] 쿼리를 실행하고 웹 사이트를 찾을 수 없는지 확인합니다.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 웹 사이트 구성에서 잘못된 행을 삭제하려면 이 [!DNL MySQL] 문을 실행하십시오.

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

솔루션이 작동하는지 확인하려면 `bin/magento` 명령을 다시 실행하십시오. 더 이상 오류가 표시되지 않아야 하며 성공적으로 배포할 수 있습니다.

## 관련 읽기

* [Adobe Commerce 배포 문제 해결사](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [Cloud UI에 &quot;로그 스니핑된&quot; 오류가 있는 경우 배포 로그 확인](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
