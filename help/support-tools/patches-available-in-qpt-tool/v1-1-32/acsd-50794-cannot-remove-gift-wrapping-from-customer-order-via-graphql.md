---
title: 'ACSD-50794: GraphQL을 통해 고객 주문에서 선물 포장을 제거할 수 없음'
description: ACSD-50794 패치를 적용하여 사용자가 GraphQL을 통해 고객 주문에서 선물 포장을 제거할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: GraphQL을 통해 고객 주문에서 선물 포장을 제거할 수 없음

ACSD-50794 패치는 사용자가 GraphQL을 통해 고객 주문에서 선물 포장을 제거할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-50794입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL을 통해 고객 주문에서 선물 포장을 제거할 수 없습니다.

<u>재현 단계</u>:

1. 프론트엔드에서 고객을 만듭니다.
1. 간단한 제품을 만듭니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]**(으)로 이동하여 *[!UICONTROL Gift Messages]*&#x200B;을(를) 활성화하고 *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*&#x200B;을(를) 설정합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**(으)로 이동하여 *[!UICONTROL Gift Wrapping]*&#x200B;을(를) 만듭니다.
1. 고객 토큰을 가져옵니다.
1. 빈 장바구니 customerCart를 만듭니다.
   * 장바구니에 제품 추가: `addProductsToCart` 돌연변이
   * 청구 주소 설정: `setBillingAddressOnCart` 돌연변이
   * 배송 주소 설정: `setShippingAddressesOnCart` 돌연변이
   * 배송 방법 설정: `setShippingMethodsOnCart` 돌연변이(평탄)
   * 결제 방법 설정: `setPaymentMethodOnCart` 돌연변이(checkmo)
1. 이제 이 장바구니 쿼리를 사용하여 선물 포장 *Uid*&#x200B;을(를) 확인하세요.

   <pre><code class="language-GraphQL">
    {
      cart(cart_id: "{{CART_ID}}") {
        available_gift_wrappings{
            uid
        }
    }
    }
    </code></pre>

1. `setGiftOptionsOnCart`을(를) 사용하여 선물 포장을 설정합니다.
1. 장바구니: 장바구니 쿼리를 확인합니다.
1. `setGiftOptionsOnCart`을(를) 사용하여 선물 포장을 설정 해제합니다(값을 null로 설정).
1. 장바구니: 장바구니 쿼리를 다시 확인하십시오.
1. 주문: `placeOrder` 돌연변이.
1. 고객 질의 실행: 고객.

   <pre><code class="language-graphql">
    query {
      customer {
        firstname
        middlename
        lastname
        suffix
        email
        orders {
            items {
                order_date
                gift_wrapping {
                    design
                    uid
                }
            }
        }
        addresses {
          firstname
          middlename
          lastname
          street
          city
          region {
            region_code
            region
          }
          postcode
          country_code
          telephone
        }
      }
    }
    </code></pre>

<u>예상 결과</u>:

사용자가 선물 포장을 설정하고 설정을 해제하면 고객 쿼리가 null을 반환합니다.

<u>실제 결과</u>:

고객 쿼리는 적용된 선물 포장을 여전히 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
