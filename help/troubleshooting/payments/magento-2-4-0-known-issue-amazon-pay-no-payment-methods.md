---
title: 'Adobe Commerce 2.4.0 알려진 문제: Amazon pay, 결제 방법 없음'
description: 이 문서에서는 고객이 Adobe Commerce 결제를 활성화한 후 **표준 체크아웃으로 돌아가기**를 사용할 때 결제 방법이 누락되는 Amazon 2.4.0 알려진 문제에 대한 해결 방법을 제공합니다.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 알려진 문제: Amazon pay, 결제 방법 없음

이 문서에서는 고객이 을 사용할 때 결제 방법이 누락된 것으로 알려진 Adobe Commerce 2.4.0 문제에 대한 해결 방법을 제공합니다 **표준 체크아웃으로 돌아가기**: Amazon pay를 활성화한 후.

## 영향을 받는 제품 및 버전

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure v2.3.5.p1 및 v2.4.0

<u>재현 단계:</u>

1. 상점 앞으로 이동합니다.
1. 장바구니에 품목을 추가하고 체크아웃을 진행합니다.
1. Amazon 결제 계정에 로그인합니다.
1. 주소를 선택하고 체크아웃을 진행합니다.
1. 클릭 **표준 체크아웃으로 돌아가기**.
1. 체크아웃을 진행합니다.

<u>예상 결과:</u>

결제 방법은 체크아웃을 다시 시작한 후에 표시해야 합니다.

<u>실제 결과:</u>

결제 방법이 누락되었습니다.

## 솔루션

2.4.1에 대한 해결이 예정되어 있습니다.

## 지원 기술 자료의 관련 자료:

* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 알려진 문제: 다중 배송 체크아웃에서 보상 포인트를 제거할 때 404 오류 발생](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0의 배송 라벨 작성 알려진 문제](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;내 장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
