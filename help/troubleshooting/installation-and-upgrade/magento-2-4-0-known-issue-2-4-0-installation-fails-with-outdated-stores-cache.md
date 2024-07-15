---
title: 오래된 저장소 캐시로 Adobe Commerce 2.4.0 설치에 실패함
description: "이 문서에서는 다음과 같은 오류 메시지와 함께 Adobe Commerce 2.4.0 설치에 실패하는 문제에 대한 해결 방법을 제공합니다. *기본 웹 사이트가 정의되지 않음. 웹 사이트를 설정하고 다시 시도하십시오.* 콘솔에 표시됩니다."
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 오래된 저장소 캐시로 Adobe Commerce 2.4.0 설치에 실패함

이 문서에서는 다음과 같은 오류 메시지와 함께 Adobe Commerce 2.4.0 설치에 실패하는 문제에 대한 해결 방법을 제공합니다. *기본 웹 사이트가 정의되지 않았습니다. 웹 사이트를 설정하고 다시 시도하십시오.*&#x200B;이(가) 콘솔에 표시됩니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0

## 문제

<u>필수 구성 요소:</u>
CLI 명령의 저장소 모듈에 대한 API에 종속성이 있는 타사 확장은 `composer.json`에서 필요에 따라 구성됩니다. 이로 인해 Adobe Commerce 2.4.0을 설치하지 못하고 다음 오류 메시지가 표시됩니다. *기본 웹 사이트가 정의되지 않았습니다. 웹 사이트를 설정하고 다시 시도하십시오.*&#x200B;이(가) 콘솔에 표시됩니다.

## 원인

CLI 명령의 저장소에 종속된 타사 확장의 경우 문제가 나타납니다. 하나는 Amazon Sales Channel 입니다.

## 솔루션

Adobe Commerce 2.4.0을 설치하기 전에 판매자는 다음을 수행해야 합니다.

1. `composer.json`에서 이러한 타사 확장을 제거합니다.
1. 확장 없이 Adobe Commerce을 설치합니다.
1. 설치 후 확장을 추가합니다.

이 문제는 2.4.1 릴리스 범위에서 수정됩니다.

## 지원 기술 자료의 관련 자료:

* [Adobe Commerce 2.4.0 알려진 문제: Klarna에 &quot;환불&quot; 레이블이 없음](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0 알려진 문제: 관리자의 새 주문 만들기 페이지에 두 개의 버튼이 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo 부분 송장 문제 활성화](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 알려진 문제: Amazon Pay 사용, 표준 체크아웃으로 돌아가기 사용 시 결제 방법 누락](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 알려진 문제: 다중 배송 체크아웃에서 보상 포인트를 제거할 때 404 오류 발생](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0의 배송 라벨 작성 알려진 문제](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;내 장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
