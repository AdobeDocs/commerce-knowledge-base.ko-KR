---
title: 'Adobe Commerce 2.4.0 알려진 문제: 새 주문 만들기 버튼이 없음'
description: 이 문서에서는 주문 생성 페이지에 있는 두 개의 누락된 단추에 대한 Commerce 관리자의 알려진 문제에 대한 해결 방법을 제공합니다. 신규 또는 기존 고객에 대한 신규 주문을 생성할 때 **SKU별 제품 추가** 및 **제품 추가** 버튼이 누락되어 카탈로그의 주문에 제품을 추가할 수 없습니다. 이는 JS 번들링이 활성화되어 있기 때문입니다. Adobe Commerce 2.4.1에서 수정 사항을 사용할 수 있습니다.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 알려진 문제: 새 주문 만들기 버튼이 없음

이 문서에서는 주문 생성 페이지에 있는 두 개의 누락된 단추에 대한 Commerce 관리자의 알려진 문제에 대한 해결 방법을 제공합니다. 새 고객이나 기존 고객에 대한 새 주문을 만들 때 **SKU별 제품 추가** 및 **제품 추가** 단추가 없기 때문에 카탈로그의 주문에 제품을 추가할 수 없습니다. 이는 JS 번들링이 활성화되어 있기 때문입니다. Adobe Commerce 2.4.1에서 수정 사항을 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>재현 단계</u>

1. **고객 > 모든 고객**(으)로 이동합니다.
1. 고객의 **편집** 링크를 클릭합니다.
1. **순서 만들기** 단추를 클릭합니다.

<u>예상 결과</u>

**SKU별 제품 추가** 및 **제품 추가** 단추가 **새 주문 만들기** 페이지에 표시됩니다.

<u>실제 결과</u>

**새 주문 만들기** 페이지에서 **SKU별 제품 추가** 및 **제품 추가** 단추가 없습니다.

## 해결 방법

이 문제에 대한 해결 방법은 Adobe Commerce 인스턴스에 대한 JS 번들링을 비활성화하는 것입니다. 이 문제는 2020년 4분기에 릴리스될 예정인 Adobe Commerce 2.4.1에서 수정될 예정입니다.

## 지원 기술 자료의 관련 자료

* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 알려진 문제: 다중 배송 체크아웃에서 보상 포인트를 제거할 때 404 오류 발생](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
