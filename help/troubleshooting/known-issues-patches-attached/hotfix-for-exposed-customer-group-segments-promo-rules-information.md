---
title: ' [!DNL GraphQL]을(를) 통해 노출된 고객 그룹 이름, 세그먼트 및 프로모션 규칙 정보'
description: 이 문서에서는  [!DNL GraphQL]을(를) 통해 고객 그룹 이름, 고객 세그먼트 및 프로모션 규칙 정보가 노출되지 않도록 하는 핫픽스를 제공합니다.
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# [!DNL GraphQL]을(를) 통해 노출된 고객 그룹 이름, 세그먼트 및 프로모션 규칙 정보

이 문서에서는 [!DNL GraphQL]을(를) 통해 고객 그룹 이름, 고객 세그먼트 및 프로모션 규칙 정보가 노출되지 않도록 하는 핫픽스를 제공합니다. 이 문제는 Adobe Commerce 2.4.8-p1에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8

## 문제

[!UICONTROL Storefront Personalization Drop-ins]의 경우 고객 그룹 이름, 세그먼트, 장바구니 및 카탈로그 규칙과 같은 기본 정보를 표시하기 위해 새 [!DNL GraphQL] 돌연변이가 도입되었습니다. 그러나 이름에 포함된 경우 오퍼 세부 정보 또는 쿠폰 코드와 같은 중요한 데이터가 노출될 수 있습니다.

### 재현 단계

#### 사례 I: [!UICONTROL Catalog Rule]

1. *관리자* 사이드바에서 **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**(으)로 이동합니다.
1. 규칙 조건(예: 제품 속성 또는 범주)을 정의합니다.
1. 규칙을 저장하고 적용합니다.
1. 제품이 규칙 조건을 충족하는지 확인합니다.
1. 모든 규칙을 가져오려면 다음 [!DNL GraphQL] 쿼리를 실행하십시오.

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. 제품을 쿼리하여 규칙이 적용되는지 확인합니다.

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### 사례 II: [!UICONTROL Cart Rule]

1. *관리자* 사이드바에서 **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**(으)로 이동합니다.
1. 최소 장바구니 값 및 고객 그룹과 같은 조건을 설정합니다.
1. 규칙을 저장하고 적용합니다.
1. 제품을 장바구니에 추가하여 규칙을 트리거합니다.
1. [!DNL GraphQL]을(를) 사용하여 모든 장바구니 규칙을 확인합니다.

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. 규칙이 활성 장바구니에 적용되는지 확인:

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### 사례 III: [!UICONTROL Customer Group]

1. *관리자* 사이드바에서 **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**(으)로 이동합니다.
1. 예상 그룹이 있는지 확인합니다.
1. [!DNL GraphQL]을(를) 사용하여 모든 그룹을 가져옵니다.

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. 고객/게스트 그룹 확인:

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### 사례 IV: [!UICONTROL Customer Segment]&#x200B;(Adobe Commerce 전용)

1. *관리자* 사이드바에서 **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**(으)로 이동합니다.
1. 고객 기반 조건(예: 주문, 장바구니 내용)을 정의합니다.
1. 적용 가능한 범위 지정: *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* 또는 둘 다.
1. 조건이 테스트 고객과 일치하는지 확인합니다.
1. [!DNL GraphQL]을(를) 사용하여 모든 세그먼트를 확인합니다.

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. 장바구니에 적용된 세그먼트의 유효성을 검사합니다.

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>예상 결과</u>:

고객 그룹, 세그먼트 및 프로모션 규칙 정보는 [!DNL GraphQL]을(를) 통해 노출되지 않습니다.

<u>실제 결과</u>:

고객 그룹 이름, 세그먼트 및 프로모션 규칙 정보는 [!DNL GraphQL]을(를) 통해 노출됩니다.

## 솔루션

Adobe Commerce 버전에 따라 첨부된 패치를 적용합니다.

* Adobe Commerce 버전 2.4.8의 경우

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* [!DNL Magento]의 경우 Source 버전 2.4.8을 엽니다.

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
