---
title: 'ACSD-52921: GraphQL에서 품절 구성 가능한 제품에 대한 장바구니 세부 정보를 요청하는 도중 오류 발생'
description: ACSD-52921 패치를 적용하여 GraphQL에서 품절 구성 가능한 제품에 대한 장바구니 세부 정보를 요청할 때 내부 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921: GraphQL에서 품절 구성 가능한 제품에 대한 장바구니 세부 정보를 요청하는 도중 오류 발생

ACSD-52921 패치는 GraphQL에서 구성 가능한 제품 품절 시 장바구니 세부 정보를 요청할 때 내부 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52921입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL에서 구성 가능한 품절 제품을 장바구니에 세부 요청하면 내부 오류가 발생합니다.

<u>재현 단계</u>:

1. 몇 가지 옵션을 사용하여 구성 가능한 제품을 만듭니다.
1. 위의 구성 가능한 제품에 대한 옵션을 프론트엔드에서 장바구니에 추가합니다(게스트 체크아웃).
1. 위에서 만든 견적에 대한 `[ quote_id_mask ]` db 테이블에서 `[ masked_id ]`을(를) 가져옵니다.
1. 다음 GraphQL 쿼리를 실행하여 위의 게스트 장바구니 세부 정보를 가져옵니다.

   쿼리의 3단계에서 받은 `[ masked_id ]`을(를) 추가합니다.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. 이렇게 하면 문제 없이 견적 세부 정보가 반환됩니다.
1. 백엔드로 이동하여 구성 가능한 제품의 *[!UICONTROL Stock Status]*&#x200B;을(를) *[!UICONTROL Out of Stock]*(으)로 업데이트합니다.
1. 4단계에서 수행한 것과 동일한 GraphQL 쿼리를 실행합니다.

<u>예상 결과</u>:

오류 메시지가 응답에서 올바르게 전송/처리됩니다.

<u>실제 결과</u>:

GraphQL 쿼리에 대한 응답으로 *500 내부 서버* 오류가 throw됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
