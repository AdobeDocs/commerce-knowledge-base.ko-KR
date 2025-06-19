---
title: 성능 저하를 방지하기 위해 캐시 활성화
description: 이 문서에서는 특정 Adobe Commerce 캐시 유형이 비활성화되어 있어 발생하는 느린 사이트 문제를 해결하는 방법에 대해 설명합니다.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: bd6aa238ff8273c60a4cf5160fb614de6ff00d21
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 성능 저하를 방지하기 위해 캐시 활성화

이 문서에서는 특정 Adobe Commerce 캐시 유형이 비활성화되어 있어 발생하는 느린 사이트 문제를 해결하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce 온-프레미스 2.2.x, 2.3.x

## 문제

성능 저하가 나타납니다. 예를 들어 체크아웃 페이지가 느리게 로드되거나 New Relic에서 Apdex 값이 감소합니다.

## 원인

성능 저하의 한 가지 이유는 특정 Adobe Commerce 캐시 유형이 비활성화되었기 때문일 수 있습니다.

## 솔루션

1. 먼저 Adobe Commerce 캐시의 상태를 확인하여 문제가 있는지 확인합니다. 이를 위해 [환경에 SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh)를 실행하고 다음 명령을 실행하십시오.

   ```bash
   php bin/magento cache:status
   ```

   각 캐시 유형의 상태가 표시됩니다( 비활성화의 경우 &quot;0&quot;, 활성화의 경우 &quot;1&quot;). 또는 `app/etc/env.php` 파일에서 이 정보를 가져올 수 있습니다.

1. 비활성화된 캐시 유형을 조사합니다. Adobe에서 대체 지침을 받지 않은 경우 모든 Adobe Commerce 캐시 유형을 활성화해야 합니다. 타사 확장을 사용하려면 Adobe Commerce 캐시를 비활성화할 필요가 없습니다.
1. 검사 결과 실수로 일부 캐시 유형을 사용하지 않도록 설정한 경우 각 캐시 유형에 대해 다음 명령을 실행하여 사용하도록 설정하십시오. `php bin/magento cache:enable <your_disabled_cache_type>`

특정 Adobe Commerce 캐시 유형을 비활성화할 수 있는지 또는 비활성화해야 하는지에 대한 우려 및/또는 질문이 있는 경우 [Adobe Commerce 지원 센터에 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 권장 사항을 요청하십시오.

## 관련 읽기

Adobe Commerce 캐시 설명서 의 개발자 설명서:

* [Adobe Commerce 캐시 개요](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [캐시 관리](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-cache)

성능 문제와 그에 대한 솔루션에 대한 기타 가능한 이유는 다음과 같습니다.

* [사이트 성능을 개선하기 위해 Adobe Commerce 배너 출력을 사용하지 않도록 설정](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [MySQL 테이블이 너무 큽니다.](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [성능 저하, 느리고 오래 실행되는 크론](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [성능 문제를 일으키는 제한된 관리자 액세스](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
