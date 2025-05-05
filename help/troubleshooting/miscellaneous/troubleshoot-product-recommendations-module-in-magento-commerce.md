---
title: Adobe Commerce에서 [!UICONTROL Product Recommendations] 모듈 문제 해결
description: 이 문서에서는 Adobe Commerce의 [!UICONTROL Product Recommendations] 모듈에 대한 문제 해결 제안에 대해 설명합니다.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Adobe Commerce에서 [!UICONTROL Product Recommendations] 모듈 문제 해결

이 문서에서는 문제 해결 제안에 대해 설명합니다.

```php
magento/product-recommendations
```

모듈 및 해당 종속성

```php
saas-export
```

모듈. Adobe Commerce에서 [!UICONTROL Product Recommendations] 도구를 사용하려면 두 모듈이 모두 작동해야 하기 때문입니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.4 - 2.4.7

## 제품 권장 사항 모듈 문제 해결

다음을 구성한 경우

```php
magento/product-recommendations
```

모듈이 올바르지만(개발자 설명서에서 [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure)을(를) 확인하십시오.) 권장 사항이 표시되지 않으면 다음을 시도하십시오.

* 모듈에서 동작 데이터를 수집할 시간이 충분하지 않았을 수 있습니다. 시스템이 데이터 수집을 시작할 수 있도록 24시간 동안 실행되도록 허용합니다. &quot;*이와 유사한 항목*&quot;과(와) 같이 동작 데이터가 필요하지 않은 권장 사항 유형을 배포하는 것이 좋습니다.

* 구성한 권장 사항이 표시되지 않는 경우 사용자에 대한 권장 사항을 빌드할 데이터가 아직 충분하지 않을 수 있습니다.

* [!DNL SaaS] 데이터 공간 또는 [!DNL API] 키가 올바른지 확인하십시오. 제품 권장 사항을 초기화하는 동안 [!DNL SaaS] Data Space 또는 [!DNL API] 키를 지정한 후 오류가 발생하면 사용자 안내서에서 [[!DNL SaaS] Data Space 및 [!DNL API] key](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas)을(를) 올바르게 입력했는지 확인하십시오. [!DNL MageID] 및 [!DNL API] 키가 연결되어 있는지 확인하려면 [!DNL MageID]을(를) 담당하는 사용자, 일반적으로 Adobe Commerce 라이선스를 담당하는 사용자가 [!DNL API] 키를 생성하는 사용자와 같아야 합니다. 사용한 [!DNL MageID]을(를) 변경해야 하는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

>[!NOTE]
>
>[**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law)(사용 안내서)이 *enabled*인 경우 Adobe Commerce은 구매자가 동의할 때까지 행동 데이터를 수집하지 않습니다.**[!UICONTROL Cookie Restriction Mode]**&#x200B;이(가) *비활성화됨*인 경우 Adobe Commerce은 기본적으로 동작 데이터를 수집합니다.

## 카탈로그 [!DNL SaaS] 내보내기 모듈

카탈로그 [!DNL SaaS] 내보내기와 관련된 문제(

```php
saas-export
```

) 모듈:

1. 개발자 설명서에서 [[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) 작업이 실행 중인지 확인하십시오.
1. 개발자 설명서에서 [[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)이(가) 실행 중인지 확인하고    ```php    Product Feed    ```    [!UICONTROL indexer]이(가) 다음으로 설정됨:    ```php    Update by Schedule    ```    .
1. 모듈이 *활성화됨*&#x200B;인지 확인하십시오. 다음    ```php    saas-export    ```    metapackage는 *enabled*&#x200B;여야 하는 다음 모듈을 설치합니다.    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. 개발자 설명서에서 [로그](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging)를 확인하십시오. 위의 모듈과 관련된 오류가 없는지 확인합니다.
1. [!UICONTROL Configuration cache]을(를) 새로 고칩니다. **시스템** > **도구** > **캐시 관리**(으)로 이동하여 [!UICONTROL Configuration cache]을(를) 지웁니다.
1. `cde_products_products_feed` 데이터베이스 테이블에 데이터가 있는지 확인하십시오.

   >[!NOTE]
   >
   >해당 테이블을 찾을 수 없으면 `catalog_data_exporter_products` 테이블을 확인하세요. 테이블 이름이 [!DNL Data Export] 버전 103.3.0 릴리스에서 변경되었습니다.

## 이벤트

개발자 설명서에서 [이벤트 컬렉션 확인](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify)은(는) Adobe Commerce으로 전송되는 동작 이벤트를 설명합니다.

## 관련 읽기

* 개발자 설명서에서 [제품 Recommendations 관리자 개발](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
* Product Recommendations 안내서의 [Product Recommendations 소개](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview)
* Product Recommendations 안내서의 [Product Recommendations 만들기](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create)
* [!DNL SaaS] 데이터 내보내기 가이드의 [로그 검토 및 문제 해결](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging)
* [!DNL SaaS] 서비스에 대한 Adobe Commerce 데이터 내보내기 안내서의 [[!DNL SaaS] 데이터 내보내기 확장 릴리스 노트](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

