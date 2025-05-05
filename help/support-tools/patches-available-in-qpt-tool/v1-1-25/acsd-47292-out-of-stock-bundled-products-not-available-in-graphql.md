---
title: 'ACSD-47292: GraphQL 응답에서 품절 번들 제품을 사용할 수 없습니다.'
description: ACSD-47292 패치를 적용하여 "재고 부족 제품 표시"가 예로 설정되어 있더라도 GraphQL 응답에서 재고 부족 번들 제품을 사용할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: 377dc62f-d1cd-4292-b25d-53c498b772a9
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-47292: GraphQL 응답에서 품절 번들 제품을 사용할 수 없습니다.

ACSD-47292 패치는 [!UICONTROL Display Out-of-Stock Products]이(가) *[!UICONTROL Yes]*(으)로 설정되어 있어도 GraphQL 응답에서 품절 번들 제품을 사용할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47292입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Display Out-of-Stock Products]이(가) *[!UICONTROL Yes]*(으)로 설정되어 있어도 GraphQL 응답에서 품절 번들 제품을 사용할 수 없습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자 > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**(으)로 이동하여 [!UICONTROL Display Out-of-Stock Products]을(를) *[!UICONTROL Yes]*(으)로 설정합니다.
1. 두 개의 간단한 제품인 s1과 s2를 만듭니다.
1. s1을 품절 및 개별적으로 표시되지 않도록 하고 s2를 품절 및 개별적으로 표시되지 않도록 한 다음 범주에 할당합니다.
1. 하나 이상의 옵션 제품이 있는 번들 제품을 만들고 s1 및 s2를 이 옵션(입력 유형 &quot;RadioButton&quot;)에 할당합니다.
1. 번들 제품을 저장하고 카테고리에 할당합니다.
1. 상점으로 가서 이 묶음상품을 열어보세요. 품절 옵션 s1이 회색으로 표시되지만 표시됩니다.
1. GraphQL 요청 보내기:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>예상 결과</u>:

[!UICONTROL Display Out-of-Stock Products]이(가) *[!UICONTROL Yes]*(으)로 설정되어 상점 앞에 표시되므로 s1 번들 옵션은 GraphQL 응답에 나열되어 있습니다.

<u>실제 결과</u>:

s1 번들 옵션이 GraphQL 응답에 나열되지 않습니다.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
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
