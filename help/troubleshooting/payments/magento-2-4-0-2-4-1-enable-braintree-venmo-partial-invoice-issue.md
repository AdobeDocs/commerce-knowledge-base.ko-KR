---
title: 'Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo 부분 송장 활성화'
description: 이 문서에서는 알려진 Adobe Commerce 2.4.0 및 2.4.1 문제에 대해 설명합니다. 여기서 Venmo를 통해 Braintree을 사용하여 수행한 주문에 대해 부분 송장을 사용할 수 없습니다.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo 부분 송장 활성화

이 문서에서는 알려진 Adobe Commerce 2.4.0 및 2.4.1 문제에 대해 설명합니다. 여기서 Venmo를 통해 Braintree을 사용하여 수행한 주문에 대해 부분 송장을 사용할 수 없습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0 및 2.4.1
* 클라우드 인프라 2.4.0 및 2.4.1의 Adobe Commerce

## 문제

<u>필수 구성 요소:</u>

Braintree 결제 방법 구성에서 **결제 작업** = *인증*; **Braintree 결제를 위한 자격 증명 모음 사용** = *아니요*(으)로 **카드를 통한 Venmo 사용** = *예*&#x200B;을(를) 설정합니다.

<u>재현 단계:</u>

1. Venmo(Braintree)를 결제 수단으로 사용하여 두 개 이상의 제품에 대한 주문을 만듭니다.
1. Commerce 관리자에서 주문을 엽니다.
1. 주문된 제품 중 하나에 대한 송장을 생성합니다.
1. 나머지 주문 제품에 대한 송장을 생성해 보십시오.

<u>예상 결과:</u>

송장이 생성되었습니다.

<u>실제 결과:</u>

다음 오류 메시지가 표시됩니다. *&quot;vault\_capture&quot; 명령이 없습니다. 명령을 확인하고 다시 시도하십시오.*

## 해결 방법

Venmo를 통해 Braintree을 사용하여 수행한 주문에 대한 송장을 생성할 때 전체 금액을 캡처합니다.
