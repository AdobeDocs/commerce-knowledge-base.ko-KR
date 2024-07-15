---
title: Adobe Commerce의 Product Recommendations 모듈 문제 해결
description: 이 문서에서는 문제 해결 제안에 대해 설명합니다.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Adobe Commerce의 Product Recommendations 모듈 문제 해결

이 문서에서는 문제 해결 제안에 대해 설명합니다.

```php
magento/product-recommendations
```

모듈 및 해당 종속성

```php
saas-export
```

모듈. Adobe Commerce에서 제품 Recommendations 도구를 사용하려면 두 모듈이 모두 작동해야 하기 때문입니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.4 - 2.4.7

## 제품 권장 사항 모듈 문제 해결

다음을 구성한 경우

```php
magento/product-recommendations
```

모듈이 올바르지만(개발자 설명서에서 [제품 Recommendations - Recommendations 설치 및 구성](https://devdocs.magento.com/recommendations/install-configure.html) 확인) 권장 사항이 표시되지 않으면 다음을 시도해 보십시오.

* 모듈이 행동 데이터를 수집하기에 충분한 시간을 갖지 못했을 가능성이 있다. 시스템이 데이터 수집을 시작할 수 있도록 24시간 동안 실행되도록 허용합니다. &quot;More like this&quot;와 같은 동작 데이터가 필요하지 않은 권장 사항 유형 배포를 고려합니다.

* 구성한 권장 사항이 표시되지 않는 경우 사용자에 대한 권장 사항을 빌드할 데이터가 아직 충분하지 않을 수 있습니다.

* SaaS 데이터 공간 또는 API 키가 유효한지 확인합니다. 제품 권장 사항을 초기화하는 동안 SaaS Data Space 또는 API 키를 지정한 후 오류가 발생하면 [SaaS Data Space 및 API 키](https://docs.magento.com/user-guide/configuration/services/saas.html)(사용 안내서)를 올바르게 입력했는지 확인하십시오. MageID 및 API 키가 연결되었는지 확인하려면 MageID를 소유한 사용자, 일반적으로 Adobe Commerce 라이선스를 소유한 사용자가 API 키를 생성하는 사용자와 동일한 사용자여야 합니다. 사용된 MageID를 변경해야 하는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

>[!NOTE]
>
>[쿠키 제한 모드](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html)(사용 안내서)가 활성화된 경우, Adobe Commerce은 구매자가 동의할 때까지 행동 데이터를 수집하지 않습니다. 쿠키 제한 모드 가 비활성화되면 Adobe Commerce은 기본적으로 동작 데이터를 수집합니다.

## 카탈로그 SaaS 내보내기 모듈

카탈로그 SaaS 내보내기와 관련된 문제의 경우(

```php
saas-export
```

) 모듈:

1. 개발자 설명서에서 [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) 작업이 실행 중인지 확인하십시오.
1. [인덱서](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)(개발자 설명서에서)가 실행 중이며    ```php    Product Feed    ```    인덱서가 (으)로 설정됨    ```php    Update by Schedule    ```    .
1. 모듈이 활성화되었는지 확인합니다. 다음    ```php    saas-export    ```    metapackage는 다음 모듈을 설치하며, 이 모듈은 모두 활성화되어야 합니다.    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. 개발자 설명서에서 [로그](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html)를 확인하십시오. 위의 모듈과 관련된 오류가 없는지 확인합니다.
1. 구성 캐시를 새로 고칩니다. **시스템** > **도구** > **캐시 관리**(으)로 이동하여 구성 캐시를 지웁니다.
1. 에 데이터가 있는지 확인합니다.    ```php    catalog_data_exporter_products    ```    데이터베이스 테이블.

## 이벤트

개발자 설명서에서 [권장 이벤트](https://devdocs.magento.com/recommendations/verify.html)는 Adobe Commerce으로 전송되는 동작 이벤트에 대해 설명합니다.

## 관련 읽기

* 개발자 설명서의 [제품 Recommendations - 개요](https://devdocs.magento.com/recommendations/product-recs.html)
* 개발자 설명서에서 [제품 Recommendations - Recommendations 설치 및 구성](https://devdocs.magento.com/recommendations/install-configure.html)
* 사용 안내서의 [마케팅 - 제품 Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html)
* 사용 안내서에서 [제품 Recommendations 만들기](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html)
