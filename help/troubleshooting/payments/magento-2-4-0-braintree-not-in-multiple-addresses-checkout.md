---
title: 'Adobe Commerce 2.4.0: Braintree이 여러 주소 체크아웃에 없음'
description: 이 문서에서는 다중 주소 체크아웃 작업에 Braintree 결제 방법이 포함되지 않는 Adobe Commerce 2.4.0 알려진 문제에 대한 해결 방법을 제공합니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree이 여러 주소에 있지 않음 체크아웃

이 문서에서는 다중 주소 체크아웃 작업에 Braintree 결제 방법이 포함되지 않는 Adobe Commerce 2.4.0 알려진 문제에 대한 해결 방법을 제공합니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.

참고: Adobe Commerce에서는 PSD 규정 준수를 유지하기 위해 버전 2.3 이상용 [Commerce Marketplace Braintree 확장](https://marketplace.magento.com/paypal-module-braintree.html)을 사용하는 것이 좋습니다. 확장 프로그램은 다중 주소 체크아웃 기능을 제공하지 않습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 v2.4.0
* 클라우드 인프라의 Adobe Commerce v2.4.0

## 문제

<u>필수 구성 요소</u>:

핵심 Braintree 통합이 사용됩니다.

<u>재현 단계</u>:

1. 가게 앞쪽으로 가보세요
1. 고객으로 로그인.
1. 장바구니에 제품을 추가합니다.
1. 장바구니를 엽니다.
1. **장바구니 보기 및 편집**&#x200B;을 누릅니다.
1. **여러 주소로 체크 아웃**&#x200B;을 누르십시오.
1. **배송 정보로 이동**&#x200B;을 누르십시오.
1. **결제 정보 계속**&#x200B;을 누르십시오.

<u>예상 결과</u>:

Braintree은 결제 방법으로 사용할 수 있습니다.

<u>실제 결과</u>:

Braintree은 결제 방법으로 사용할 수 없습니다.

## 해결 방법

Adobe Commerce 2.4.0에서 Braintree을 사용하는 경우 다중 주소 옵션을 활성화하지 마십시오. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.

## 지원 기술 자료의 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
