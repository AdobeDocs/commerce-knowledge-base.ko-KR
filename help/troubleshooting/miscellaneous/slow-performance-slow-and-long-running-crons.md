---
title: 성능 저하, 느리고 오래 실행되는 크론
description: 이 문서에서는 플랫 테이블 및 인덱서가 활성화되었기 때문에 사이트 성능 문제와 느린 실행 및 멈춤 크론을 해결하는 방법에 대해 설명합니다.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 성능 저하, 느리고 오래 실행되는 크론

>[!WARNING]
>
>모든 Adobe Commerce 버전에서 일부 확장은 플랫 테이블에서만 작동하므로 플랫 테이블을 비활성화하면 위험이 있습니다. 플랫 카탈로그 인덱서를 사용하는 확장이 있는 경우 해당 값을 &quot; *아니요*&quot;(으)로 설정할 때 이를 고려해야 할 수 있습니다.

이 문서에서는 [플랫 테이블 및 인덱서](https://experienceleague.adobe.com/ko/docs/commerce-admin/catalog/catalog/catalog-flat)가 활성화되었기 때문에 사이트 성능 문제와 느린 실행 및 멈춤 크론을 해결하는 방법에 대해 설명합니다.

영향을 받는 제품 및 버전

* cloud infrastructure 2.1.x 이상 버전의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.1.x 이상
* Magento Open Source 2.1.x 이상

## 문제

플랫 인덱서로 인해 다음이 발생할 수 있습니다.

* 많은 SQL 로드 및 사이트 성능 문제
* 오래 달리고 크론에 갇혀 있습니다.

## 원인

플랫 테이블 및 인덱서가 활성화되었습니다.

## 솔루션 {#solution}

Adobe Commerce 및 Magento Open Source 2.1.x 이상부터 플랫 카탈로그를 사용하는 것이 더 이상 모범 사례가 아니므로 권장되지 않습니다. 이 기능을 계속 사용하면 성능 저하 및 기타 인덱싱 문제가 발생하는 것으로 알려져 있습니다. 플랫 카탈로그를 비활성화하려면 다음을 수행합니다.

1. 관리자에서 **스토어** > **설정** > **구성**&#x200B;으로 이동합니다.
1. **카탈로그** 아래의 왼쪽 패널에서 **카탈로그**&#x200B;를 선택합니다.
1. **Storefront** 섹션을 확장하고 다음을 수행합니다.
   * **일반 카탈로그 범주 사용**&#x200B;을 *아니요*(으)로 설정합니다.
   * **기본 카탈로그 제품 사용**&#x200B;을 *아니요*(으)로 설정합니다.
1. 완료되면 **구성 저장**&#x200B;을 클릭하세요. 그런 다음 메시지가 표시되면 캐시를 새로 고칩니다.
1. `php bin/magento cache:flush`을(를) 실행하여 캐시를 플러시합니다.

옵션이 회색으로 표시되어 **일반 카탈로그 범주 사용** 및 **일반 카탈로그 제품 사용**&#x200B;을 *아니요*(으)로 변경할 수 없는 경우 `app/etc/config.php`에서 일반 인덱서를 사용하지 않도록 설정하십시오.

1. 이 명령을 실행하여 모든 인덱서가 일정별로 업데이트되도록 설정합니다. `php bin/magento indexer:set-mode schedule`.
1. `app/etc/config.php`을(를) 편집하고 `flat_catalog_product` 및 `flat_catalog_category`이(가) 있는 줄을 찾습니다. 줄을 비활성화하려면 1에서 0으로 변경하십시오.
1. `php bin/magento app:config:import` 명령 실행
1. 이 명령을 실행하여 플랫 인덱서가 비활성화되었는지 확인합니다. `php        bin/magento indexer:status`.
1. `php bin/magento cache:flush`을(를) 실행하여 캐시를 플러시합니다.

## 관련 정보

지원 기술 자료에서 [중단된 Adobe Commerce cron 작업을 클라우드에서 수동으로 재설정](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md).
