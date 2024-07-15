---
title: 'Adobe Commerce 2.4.0: 로컬 결제를 선택하는 동안 체크아웃 오류 발생'
description: '이 문서에서는 체크아웃 중에 일부 국가의 로컬 결제 방법을 선택할 때 오류 메시지가 표시되는 Adobe Commerce의 알려진 문제에 대한 해결 방법에 대해 설명합니다. 이는 벨기에, 이탈리아, 네덜란드, 폴란드 및 스페인에 대해 발생합니다.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: 로컬 결제를 선택하는 동안 체크아웃 오류 발생

이 문서에서는 체크아웃 중에 일부 국가의 로컬 결제 방법을 선택할 때 오류 메시지가 표시되는 Adobe Commerce의 알려진 문제에 대한 해결 방법에 대해 설명합니다. 이는 벨기에, 이탈리아, 네덜란드, 폴란드 및 스페인에 대해 발생합니다.

오류 메시지 &quot;*현재 사용 가능한 결제 방법이 없습니다. 청구 주소를 업데이트하십시오.*&quot;이(가) 표시되지만 로컬 결제 방법이 여전히 표시되고 올바르게 작동합니다. Adobe Commerce 2.4.1에서 영구 수정 사항을 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>필수 구성 요소</u>:

* Adobe Commerce 2.4.0이 설치되어 있습니다.
* 제품 하나와 범주 하나를 만듭니다.
* [Braintree 결제 방법](https://devdocs.magento.com/guides/v2.4/graphql/payment-methods/braintree.html)을 구성하십시오.

<u>재현 단계</u>:

1. 상점 앞으로 이동합니다.
1. 장바구니에 추가할 항목을 선택하십시오.
1. 체크아웃을 진행합니다.
1. 유효한 주소로 주소 양식을 작성하십시오.
1. 검토 및 지급 페이지로 이동합니다.

<u>예상 결과</u>:

로컬 결제 방법은 오류 메시지 없이 정상적으로 표시되어야 합니다.

<u>실제 결과</u>:

오류 메시지 &quot;*현재 사용 가능한 결제 방법이 없습니다. 청구 주소를 업데이트하십시오.*&quot;이(가) 표시되지만 로컬 결제 방법이 여전히 표시되고 올바르게 작동합니다.

## 솔루션

모든 현지 결제 수단이 정상적으로 작동하게 되므로 해결 방법은 표시된 오류 메시지를 무시하고 정상적으로 결제를 계속하는 것입니다. 이 수정 사항은 Adobe Commerce 버전 2.4.1부터 사용할 수 있습니다.

## 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 반환 배송 레이블을 만들 때 편집 페이지가 작동하지 않음](/help/troubleshooting/known-issues-patches-attached/magento-2-4-0-patch-returns-shipping-label-creation-issue.md)
* [Adobe Commerce 2.4.0 알려진 문제: 고객의 활동에 대한 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
