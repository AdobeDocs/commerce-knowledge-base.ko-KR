---
title: 'ACSD-57643: 사용자 지정 옵션이 GraphQL을 통해 장바구니에 잘못 추가된 제품'
description: ACSD-57643 패치를 적용하여 사용자 지정 옵션이 있는 제품이 GraphQL을 통해 장바구니에 잘못 추가되는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, GraphQL, Products
role: Admin, Developer
source-git-commit: 62c83f36440cd05fa2d7f85da3e22c9744ad75c1
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# ACSD-57643: 사용자 지정 옵션이 GraphQL을 통해 장바구니에 잘못 추가된 제품

ACSD-57643 패치는 사용자 지정 옵션이 있는 제품이 GraphQL을 통해 장바구니에 잘못 추가되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57643입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 및 Magento Open Source 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 옵션이 있는 제품이 GraphQL을 통해 장바구니에 잘못 추가되었습니다.

<u>재현 단계</u>:

1. 제품에 대한 사용자 정의 옵션 유형 필드를 만듭니다.
1. GraphQL을 사용하여 고객 토큰을 생성합니다.
1. 빈 장바구니를 만듭니다.
1. 아래 페이로드를 사용하여 제품을 장바구니에 추가합니다.

   ```graphql
   mutation {
     addProductsToCart(
       cartId: "wNVOTaE6sDCJoObZCCqikHQI3GyFaVif"
       cartItems: [
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product1 option1 "
           }]
         },
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product2 option1"
           }]
         }
         {
           quantity: 3
           sku: "24-MB01",
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x"
             value:"product3 option1"
           }]        
         }
       ]
     ) {
       cart {
         items {
           product {
             name
             sku
           }
           ... on SimpleCartItem {
             customizable_options {
               customizable_option_uid
               label
               values {
                 customizable_option_value_uid
                 value
               }
             }
           }
           quantity
         }
       }
       user_errors {
         code
         message
       }
     }
   }
   ```

1. 제품이 한 번만 추가됨을 알 수 있습니다.

   ```json
   {
     "data": {
       "addProductsToCart": {
         "cart": {
           "items": [
             {
               "product": {
                 "name": "Joust Duffle Bag",
                 "sku": "24-MB01"
               },
               "customizable_options": [
                 {
                   "customizable_option_uid": "Y3VzdG9tLW9wdGlvbi8x",
                   "label": "Option1",
                   "values": [
                     {
                       "customizable_option_value_uid": "Y3VzdG9tLW9wdGlvbi8x",
                       "value": "product1 option1"
                     }
                   ]
                 }
               ],
               "quantity": 5
             }
           ]
         },
         "user_errors": []
       }
     }
   }
   ```

<u>예상 결과</u>:

동일한 SKU에 대해 서로 다른 사용자 지정 옵션을 동시에 사용하여 제품을 장바구니에 추가할 수 있습니다.

<u>실제 결과</u>:

동일한 SKU에 대해 서로 다른 사용자 지정 옵션을 동시에 사용하여 제품을 장바구니에 추가할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.