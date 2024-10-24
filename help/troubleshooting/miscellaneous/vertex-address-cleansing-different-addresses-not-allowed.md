---
title: '꼭짓점 주소 정리: 다른 주소는 허용되지 않음'
description: 이 문서에서는 사용자가 Vertex 주소 유효성 검사가 활성화된 상태에서 **다른** 청구 및 배송 주소를 입력하려고 할 때 상점 첫 화면에서 사용자가 해당 주소를 입력할 수 없는 문제에 대한 해결 방법에 대해 설명합니다.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 정점 주소 정리: 다른 주소는 허용되지 않습니다.

이 문서에서는 사용자가 Vertex 주소 유효성 검사가 활성화된 상태에서 **다른** 청구 및 배송 주소를 입력하려고 할 때 상점 전면에서 사용자가 입력할 수 없는 문제에 대한 해결 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.5-p1

## 문제

<u>재현 단계</u>:

1. 관리자 > **스토어** > **구성** > **판매** > **주소 정리**&#x200B;로 이동합니다.
1. **꼭지점 주소 정리 사용** 드롭다운에서 *사용*&#x200B;을 선택하고 **구성 저장**&#x200B;을 선택합니다.
1. 게스트로 프론트엔드로 이동하여 제품을 장바구니에 추가합니다.
1. 장바구니 아이콘을 클릭하고 **체크아웃을 진행**&#x200B;합니다.
1. 주소 필드를 입력합니다.
1. 원하는 **배송 방법**&#x200B;을 선택하고 **다음**&#x200B;을 클릭합니다.
1. **다음** 단추를 다시 클릭합니다.
1. **내 청구 및 배송 주소** **이(가) 동일함**&#x200B;의 선택을 취소하고 새 청구 주소(주소와 다름)를 입력하십시오.
1. **업데이트** 단추를 클릭한 다음 **주소 업데이트**&#x200B;를 클릭합니다.

<u>예상 결과</u>:

사용자에게 서로 다른 청구 및 배송 주소가 표시됩니다.

<u>실제 결과</u>:

사용자가 업데이트를 누르면 청구 및 배송 주소가 동일한 주소로 복구됩니다.

## 원인

꼭지점 주소 확인에 실패했습니다.

## 솔루션

Vertex 주소 확인을 비활성화하거나 2.4.0으로 업그레이드하십시오.

## 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 알려진 문제: 다중 배송 체크아웃에서 보상 포인트를 제거할 때 404 오류 발생](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;내 장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: Klarna에 &quot;환불&quot; 레이블이 없음](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0 알려진 문제: 관리자의 새 주문 만들기 페이지에 두 개의 버튼이 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree이 활성화되면 Venmo 부분 송장 문제](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 알려진 문제: Amazon Pay 사용, 표준 체크아웃으로 돌아가기 사용 시 결제 방법 누락](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 알려진 문제: 오래된 저장소 캐시로 2.4.0 설치에 실패함](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
