---
title: 'Adobe Commerce 2.4.1: PayPal Braintree 게스트 체크아웃에서 잘못된 메시지'
description: 이 문서에서는 게스트 체크아웃이 비활성화된 경우 Braintree을 통해 PayPal로 주문하려는 게스트 고객에게 유익하지 않은 오류 메시지가 표시되는 알려진 Adobe Commerce 2.4.1 문제에 대해 설명합니다.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: PayPal-Braintree 게스트 체크아웃 시 잘못된 메시지

이 문서에서는 게스트 체크아웃이 비활성화된 경우 Braintree을 통해 PayPal로 주문하려는 게스트 고객에게 유익하지 않은 오류 메시지가 표시되는 알려진 Adobe Commerce 2.4.1 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0, 2.4.1
* 클라우드 인프라 2.4.0, 2.4.1의 Adobe Commerce

## 문제

백엔드에서 게스트 체크아웃이 비활성화되고 PayPal through Braintree 결제 옵션이 Mini-Cart 또는 Shopping Cart에서 선택되면 구체적이지 않은 오류가 표시됩니다.

<u>필수 구성 요소</u>:

1. Commerce 관리자의 **스토어** > **구성** > **판매** > **체크아웃**&#x200B;에서 **게스트 체크아웃 허용** = *아니요*&#x200B;를 설정하십시오.
1. 사용 안내서의 [Braintree](https://docs.magento.com/user-guide/payment/braintree.html?)에 설명된 대로 Braintree을 통해 PayPal을 사용하도록 설정하십시오.

<u>재현 단계</u>:

1. 장바구니에 제품을 게스트로 추가합니다.
1. **미니 장바구니**&#x200B;를 선택하고 **PayPal로 결제**&#x200B;를 클릭하세요.
1. Paypal 체크아웃을 완료하면 Order Review 페이지에 도달합니다.
1. **배송 방법**&#x200B;을 선택하세요.
1. **주문**&#x200B;을 클릭하세요.

<u>예상 결과</u>:

고객이 Mini-cart 또는 Shopping Cart 페이지에서 PayPal 버튼을 클릭하면 고객에게 다음과 같은 메시지가 표시됩니다.

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Braintree을 사용하지 않고 직접 Paypal을 사용하는 경우 이 시나리오는 다르게 작동합니다. 게스트 사용자가 결제 프로세스를 계속 진행할 수 없습니다. 게스트 사용자가 Mini-Cart에서 PayPal 단추를 클릭하면 다음 메시지가 표시됩니다.

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>실제 결과</u>:

고객이 장바구니 페이지로 리디렉션되고 다음 메시지가 표시됩니다.

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## 해결 방법

이 문제에 대한 해결 방법은 고객이 스토어에 로그인할 수 있다는 것입니다(로그인한 사용자는 게스트 체크아웃을 사용하지 않음). 게스트 체크아웃이 비활성화된 경우. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.

## 관련 읽기

* 지원 기술 자료에서 [Adobe Commerce의 장바구니에 있는 제품 수에 대한 모범 사례](https://support.magento.com/hc/en-us/articles/360048550332).
* [주문 처리 자습서: 1단계. 개발자 설명서에서 장바구니에 항목 추가](https://devdocs.magento.com/guides/v2.4/rest/tutorials/orders/order-add-items.html)
* [GraphQL 체크아웃 튜토리얼: 1단계. 개발자 설명서에서 장바구니에 제품 추가](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-add-product-to-cart.html)
