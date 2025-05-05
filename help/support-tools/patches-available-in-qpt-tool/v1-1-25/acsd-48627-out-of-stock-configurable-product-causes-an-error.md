---
title: "ACSD-48627: 품절 구성 가능한 제품에서 오류가 발생합니다."
description: ACSD-48627 패치를 적용하여 장바구니 세부 정보를 가져오기 위해 GraphQL 요청을 보낼 때 품절 구성 가능한 제품으로 인해 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
exl-id: e3048a91-1112-49a7-afcc-e6bb23208351
feature: Admin Workspace, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-48627: 품절 구성 가능한 제품으로 인해 오류가 발생합니다.

ACSD-48627 패치는 장바구니 세부 정보를 가져오기 위해 GraphQL 요청을 보낼 때 품절 구성 가능한 제품으로 인해 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-48627입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

품절 구성 가능한 제품으로 GraphQL 요청을 보내 장바구니 세부 정보를 가져올 때 오류가 발생합니다.

<u>재현 단계</u>:

1. 고객 계정을 만듭니다.
1. 구성 가능한 제품을 포함하여 일부 제품을 장바구니에 추가합니다.
1. 관리 백엔드로 이동하여 모든 하위 제품 수량을 0으로 설정하여 구성 가능한 제품을 편집합니다.
1. 구성 가능한 제품은 모든 하위 제품이 품절됨에 따라 품절됩니다.
1. `catalog_product_index_price` 테이블을 확인합니다. 이 제품의 레코드가 비어 있습니다.
1. 고객 토큰을 가져오기 위해 GraphQL 요청을 만듭니다.

   ```GraphQL
   mutation {
       generateCustomerToken(
           email: "test@example.com"
           password: "xxxx"
           ) {
               token
               }
               }
   ```

1. GraphQL 요청을 만들어 cartId를 가져옵니다.

   ```GraphQL
   Headers: Authentication => Bearer [customer token in step 6]
   ```

   ```GraphQL
   {
       customerCart {
           id
           items {
               id
               product {
                   name
                   sku
                   }
                   quantity
                   }
                   }
                   }
   ```

1. GraphQL을 요청하여 장바구니 세부 정보를 가져옵니다.

   ```GraphQL
   Headers: Authentication => Bearer [customer token in step 6]
   ```

   ```GraphQL
   query GetCartDetails($cartId: String!) {
       cart(cart_id: $cartId) {
           id
           ...CartPageFragment
           __typename
           }
           }
           fragment CartPageFragment on Cart {
               id
               total_quantity
               ...AppliedCouponsFragment
               ...ProductListingFragment
               ...PriceSummaryFragment
               __typename
               }
               fragment AppliedCouponsFragment on Cart {
                   id
                   applied_coupons {
                       code
                       __typename
                       }
                       __typename
                       }
                       fragment ProductListingFragment on Cart {
                           id
                           items {
                               uid
                               product {
                                   uid
                                   name
                                   sku
                                   url_key
                                   url_suffix
                                   thumbnail {
                                       url
                                       __typename
                                       }
                                       small_image {
                                           url
                                           __typename
                                           }
                                           stock_status
                                           price_range {
                                               minimum_price {
   
                                               final_price {
                                                   currency
                                                   value
                                                   __typename
                                                   }
                                                   regular_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       __typename
                                                       }
                                                       __typename
                                                       }
                                                       stock_status
                                                       ... on ConfigurableProduct {
                                                           variants {
                                                               attributes {
                                                                   uid
                                                                   __typename
                                                                   }
                                                                   product {
                                                                       uid
                                                                       small_image {
                                                                           url
                                                                           __typename
                                                                           }
                                                                           stock_status
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           prices {
                                                                               price {
                                                                                   currency
                                                                                   value
                                                                                   __typename
                                                                                   }
                                                                                   __typename
                                                                                   }
                                                                                   quantity
                                                                                   ... on
                                                                                   ConfigurableCartItem {
                                                                                       configurable_options {
                                                                                           id
                                                                                           configurable_product_option_uid
                                                                                           option_label
                                                                                           configurable_product_option_value_uid
                                                                                           value_label
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           fragment PriceSummaryFragment on Cart {
                                                                                               id
                                                                                               items {
                                                                                                   uid
                                                                                                   quantity
                                                                                                   __typename
                                                                                                   }
                                                                                                   ...ShippingSummaryFragment
                                                                                                   prices {
                                                                                                       ...TaxSummaryFragment
                                                                                                       ...DiscountSummaryFragment
                                                                                                       ...GrandTotalFragment
                                                                                                       subtotal_excluding_tax {
                                                                                                           currency
                                                                                                           value
                                                                                                           __typename
                                                                                                           }
                                                                                                           subtotal_including_tax {
                                                                                                               currency
                                                                                                               value
                                                                                                               __typename
                                                                                                               }
                                                                                                               __typename
                                                                                                               }
                                                                                                               __typename
                                                                                                               }
                                                                                                               fragment DiscountSummaryFragment on
                                                                                                               CartPrices {
                                                                                                                   discounts {
                                                                                                                       amount {
                                                                                                                           currency
                                                                                                                           value
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           label
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           fragment GrandTotalFragment on CartPrices {
                                                                                                                               grand_total {
                                                                                                                                   currency
                                                                                                                                   value
                                                                                                                                   __typename
                                                                                                                                   }
                                                                                                                                   __typename
                                                                                                                                   }
                                                                                                                                   fragment ShippingSummaryFragment on Cart {
                                                                                                                                       id
                                                                                                                                       shipping_addresses {
                                                                                                                                           selected_shipping_method {
                                                                                                                                               amount {
                                                                                                                                                   currency
                                                                                                                                                   value
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   street
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   fragment TaxSummaryFragment on CartPrices {
                                                                                                                                                       applied_taxes {
                                                                                                                                                           amount {
                                                                                                                                                               currency
                                                                                                                                                               value
                                                                                                                                                               __typename
                                                                                                                                                               }
                                                                                                                                                               __typename
                                                                                                                                                               }
                                                                                                                                                               __typename
                                                                                                                                                               }
   ```

<u>예상 결과</u>:

응답에 *내부 서버 오류*&#x200B;가 없습니다.

<u>실제 결과</u>:

응답에 *내부 서버 오류*&#x200B;가 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
