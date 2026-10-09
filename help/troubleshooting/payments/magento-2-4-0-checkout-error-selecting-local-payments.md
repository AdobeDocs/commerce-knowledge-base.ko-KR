---
title: 'Adobe Commerce 2.4.0: 로컬 결제를 선택하는 동안 체크아웃 오류 발생'
description: 이 문서에서는 체크아웃 중에 일부 국가의 로컬 결제 방법을 선택할 때 오류 메시지가 표시되는 Adobe Commerce의 알려진 문제에 대한 해결 방법에 대해 설명합니다. 이는 벨기에, 이탈리아, 네덜란드, 폴란드 및 스페인에 대해 발생합니다.
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: 로컬 결제를 선택하는 동안 체크아웃 오류 발생

이 문서에서는 체크아웃 중에 일부 국가의 로컬 결제 방법을 선택할 때 오류 메시지가 표시되는 Adobe Commerce의 알려진 문제에 대한 해결 방법에 대해 설명합니다. 이는 벨기에, 이탈리아, 네덜란드, 폴란드 및 스페인에 대해 발생합니다.

오류 메시지 &quot;*현재 사용 가능한 결제 방법이 없습니다. 청구 주소를 업데이트하십시오.*&quot; 이 표시되지만 로컬 결제 방법이 여전히 표시되고 올바르게 작동합니다. Adobe Commerce 2.4.1에서 영구 수정 사항을 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>필수 구성 요소</u>:

* Adobe Commerce 2.4.0이 설치되어 있습니다.
* 제품 하나와 범주 하나를 만듭니다.
* [Braintree 결제 방법](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/)을 구성하십시오.

<u>재현 단계</u>:

1. 상점 앞으로 이동합니다.
1. 장바구니에 추가할 항목을 선택하십시오.
1. 체크아웃을 진행합니다.
1. 유효한 주소로 주소 양식을 작성하십시오.
1. 검토 및 지급 페이지로 이동합니다.

<u>예상 결과</u>:

로컬 결제 방법은 오류 메시지 없이 정상적으로 표시되어야 합니다.

<u>실제 결과</u>:

오류 메시지 &quot;*현재 사용 가능한 결제 방법이 없습니다. 청구 주소를 업데이트하십시오.*&quot; 표시되지만 로컬 결제 방법이 여전히 표시되고 올바르게 작동합니다.

## 솔루션

모든 현지 결제 수단이 정상적으로 작동하게 되므로 해결 방법은 표시된 오류 메시지를 무시하고 정상적으로 결제를 계속하는 것입니다. 이 수정 사항은 Adobe Commerce 버전 2.4.1부터 사용할 수 있습니다.

## 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
