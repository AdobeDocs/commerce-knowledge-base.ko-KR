---
title: "'캐시 플러시 시 시 배포 실패: '캐시' 네임스페이스 오류에 정의된 명령이 없습니다.'"
description: 이 문서에서는 다음 오류**캐시 네임스페이스에 정의된 명령이 없음**과 함께 배포가 실패하는 경우의 문제에 대한 해결 방법을 제공합니다.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: e13be3ef9daa17b9463c8251933f68f6a35fedd2
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# 캐시 플러시 시 시 배포 실패: &quot;&#39;캐시&#39; 네임스페이스 오류에 정의된 명령이 없습니다.&quot;

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

**core_config_data** 테이블에 데이터베이스에 더 이상 존재하지 않는 저장소 ID 또는 웹 사이트 ID에 대한 구성이 포함되어 있습니다. 이 문제는 다른 인스턴스/환경에서 데이터베이스 백업을 가져왔을 때 발생하며, 이러한 범위에 대한 구성은 연결된 저장소/웹 사이트가 삭제되어도 데이터베이스에 남아 있습니다.

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

1. 이 MySql 쿼리를 실행하여 스토어를 찾을 수 없는지 확인합니다. 이 값은 2단계에서 오류 메시지로 표시됩니다. 

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 다음 MySql 문을 실행하여 잘못된 행을 삭제합니다. 

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

   이 MySql 쿼리를 실행하고 웹 사이트를 찾을 수 없는지 확인합니다.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 이 MySql 문을 실행하여 웹 사이트 구성에서 잘못된 행을 삭제합니다.

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

솔루션이 작동하는지 확인하려면 `bin/magento` 명령을 다시 실행하십시오. 더 이상 오류가 표시되지 않아야 하며 성공적으로 배포할 수 있습니다.

## 관련 읽기

* [Adobe Commerce 배포 문제 해결사](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html)
* [Cloud UI에 &quot;로그 스니핑&quot; 오류가 있는 경우 배포 로그 확인](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
