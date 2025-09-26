---
title: 'Adobe Commerce 2.4.0 알려진 문제: Klarna에 "환불" 레이블이 없음'
description: 이 문서에서는 Klarna VBE(공급업체 번들 확장)에 누락된 **환불** 레이블에 대한 관리자의 알려진 문제에 대한 해결 방법을 제공합니다. Klarna 포털에서 환불을 진행할 때, **Refund** 라벨이 환불된 묶음 제품 옆에 표시되지 않는다.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 알려진 문제: Klarna에 &quot;환불&quot; 레이블이 없음

이 문서에서는 Klarna VBE(공급업체 번들 확장)에 누락된 **환불** 레이블에 대한 관리자의 알려진 문제에 대한 해결 방법을 제공합니다. Klarna 포털에서 환불을 진행하는 경우, 환불된 번들 제품 옆에 **Refund** 레이블이 표시되지 않습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>필수 구성 요소:</u>

* Klarna가 활성화되었습니다.
* 번들 제품이 만들어집니다.

<u>재현 단계</u>

1. Adobe Commerce 프론트엔드로 이동하여 번들 제품을 **장바구니**&#x200B;에 추가하십시오.
1. 체크아웃으로 이동합니다.
1. 체크아웃에 소비자 정보를 입력하고 **다음**&#x200B;을 클릭합니다.
1. **KP 옵션**&#x200B;을 선택하고 **주문**&#x200B;을 클릭하세요.
1. **관리자** > **판매** > **주문**(으)로 이동합니다.
1. 주문을 엽니다.
1. 제품에 대한 송장을 생성합니다.
1. **청구서** > **청구서 선택** > **대변 메모** > **환불**(오프라인 환불&#x200B;**이 아님**) 클릭.
1. 클라르나 포털로 가
1. 주문을 엽니다.
1. **환불** 레이블이 있습니다.

<u>예상 결과</u>

Klarna 포털에서는 환불된 제품 옆에 **Refund** 레이블이 표시됩니다.

<u>실제 결과</u>

Klarna 포털에서는 환불된 제품 옆에 **Refund** 레이블이 표시되지 않습니다.

## 해결 방법

이 문제에 대한 해결 방법은 환불된 번들 제품에 대해 Klarna 포털에서 누락된 **Refund** 레이블을 무시하는 것입니다. **환불** 레이블이 표시되지 않았더라도 환불이 발생했습니다. 이 문제는 2020년 4분기에 릴리스될 예정인 Adobe Commerce 2.4.1에서 수정될 예정입니다.

## 지원 기술 자료의 관련 자료:

* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
