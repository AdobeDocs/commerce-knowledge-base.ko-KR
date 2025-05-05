---
title: 'ACSD-49973:  [!DNL GraphQL]을(를) 통해 번들 제품을 가져오는 성능이 향상되었습니다.'
description: ACSD-49973 패치를 적용하여  [!DNL GraphQL]을(를) 통해 번들 제품을 가져올 때 성능 저하가 발생하는 Adobe Commerce 문제를 해결합니다.
exl-id: 7d7fce0f-40f9-4dec-aee7-1014690ccd7c
feature: GraphQL, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-49973: [!DNL GraphQL]을(를) 통해 번들 제품을 가져오는 성능이 향상되었습니다.

ACSD-49973 패치는 [!DNL GraphQL]을(를) 통해 번들 제품을 가져오는 성능을 향상시킵니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49973입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL GraphQL]을(를) 통해 번들 제품을 가져올 때 성능이 저하됩니다.

<u>필수 구성 요소</u>:

[성능 도구 키트](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html?lang=ko)를 사용하여 2000 번들 제품을 만듭니다.

<u>재현 단계</u>:

1. [!DNL DB] 쿼리 로거 사용:

   ```
   bin/magento dev:query-log:enable
   ```

1. 다음 [!DNL GraphQL] 쿼리를 실행합니다.

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. `var/log/db.log`에서 `catalog_product_bundle_selection` 테이블에 대한 요청을 확인합니다.

<u>예상 결과</u>:

`catalog_product_bundle_selection` 테이블에 대한 요청이 `var/log/db.log`에 없어야 합니다.

<u>실제 결과</u>:

동시에 트리거되는 `catalog_product_bundle_selection` 테이블에 대한 요청이 2000개 있으므로 성능이 저하됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
