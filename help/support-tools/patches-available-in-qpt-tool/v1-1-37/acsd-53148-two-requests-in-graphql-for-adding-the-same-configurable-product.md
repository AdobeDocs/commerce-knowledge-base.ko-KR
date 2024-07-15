---
title: "ACSD-53148: 동일한 구성 가능한 제품 추가를 위한 GraphQL의 두 개의 병렬 요청"
description: ACSD-53148 패치를 적용하여 GraphQL에서 동일한 구성 가능한 제품을 장바구니에 추가하기 위한 두 개의 병렬 요청이 동일한 제품 SKU를 사용하는 장바구니에 두 개의 개별 항목을 초래하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 14290c7f-9b0a-4745-a579-5c34799b78ef
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-53148: 동일한 구성 가능한 제품 추가를 위한 GraphQL의 두 개의 병렬 요청

ACSD-53148 패치는 구성 가능한 동일한 제품을 장바구니에 추가하기 위해 GraphQL에서 두 개의 병렬 요청이 발생하면 동일한 제품 SKU를 사용하는 장바구니에 두 개의 개별 항목이 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-53148입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 동일한 제품을 장바구니에 추가하기 위해 GraphQL에서 두 개의 병렬 요청을 수행하면 동일한 제품 SKU를 사용하는 장바구니에 두 개의 개별 항목이 생성되었습니다.

<u>재현 단계</u>:

1. SKU *Test*&#x200B;로 구성 가능한 제품을 만들고 SKU *Test-A*&#x200B;로 간단한 제품을 만듭니다.
1. GraphQL을 통해 새 빈 장바구니를 만듭니다(고유한 [!DNL URL](으)로 위치 변경).

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"mutation{\n createEmptyCart\n}","variables"{}}'
   ```

1. 두 개의 동시 요청을 실행하여 장바구니에 동일한 제품을 추가합니다(두 요청의 *cartID* 및 위치 변경).

   ```GraphQL
       curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}' & curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}'
   ```

1. 장바구니를 가져와서 항목을 확인합니다(*cartId* 및 위치 변경).

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"{\n cart(cart_id: \"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf\") {\n items {\n id\n product {\n name\n sku\n }\n quantity\n }\n\n }\n}\n","variables":{}}'
   ```

<u>예상 결과</u>:

항목이 [!UICONTROL qty] = 2로 한 번 나열되었습니다.

```GraphQL
    {"data":{"cart":{"items":[{"id":"5","product":{"name":"config1","sku":"config1"},"quantity":2}]}}}%
```

<u>실제 결과</u>:

항목이 [!UICONTROL qty] = 1인 상태로 두 번 나열되었습니다.

```GraphQL
    {"data":{"cart":{"items":[{"id":"1","product":
    {"name":"config1","sku":"config1"},"quantity":1},
    {"id":"3","product":{"name":"config1","sku":"config1"},"quantity":1}]}}}%
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
