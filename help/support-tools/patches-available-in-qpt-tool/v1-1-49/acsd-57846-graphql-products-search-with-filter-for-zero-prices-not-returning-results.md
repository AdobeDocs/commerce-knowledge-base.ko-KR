---
title: 'ACSD-57846: 필터를 사용하여 GraphQL 제품을 검색하면 결과가 반환되지 않음'
description: ACSD-57846 패치를 적용하여 0부터 가격으로 제품을 필터링하면  [!DNL OpenSearch] 에 잘못된 요청이 발생하고 결과가 반환되지 않는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Products
role: Admin, Developer
source-git-commit: 490c7449761ded6aef10a838f27e1ea7671c6cc8
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# ACSD-57846: 필터를 사용하여 GraphQL 제품을 검색하면 결과가 반환되지 않음

ACSD-57846 패치는 0부터 제품의 가격을 필터링하면 [!DNL OpenSearch]에 잘못된 요청이 발생하고 결과가 반환되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57846입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 제품 검색에서 제품 가격을 0에서 필터링하면 [!DNL OpenSearch]에 잘못된 형식의 요청이 발생하고 결과가 반환되지 않습니다.

<u>재현 단계</u>:

1. 두 가지 간단한 제품으로 카테고리를 만듭니다.
   * simple1 - 가격 $0
   * simple2 - 가격 $10
1. 두 제품이 프론트엔드에 모두 표시되는지 확인하십시오.
1. `price:{from:"1"}`(으)로 요청을 보냅니다.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"1"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

1. 제품 *simple2*&#x200B;을(를) 반환합니다.
1. 이제 `price:{from:"0"}`(으)로 요청을 보냅니다.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"0"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

<u>예상 결과</u>:

*simple1*&#x200B;과(와) *simple2* 제품이 모두 반환됩니다.

<u>실제 결과</u>:

반품된 제품이 없습니다.

```json
{
    "data": {
        "products": {
            "totalResult": 0,
            "productItems": []
        }
    }
}
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
