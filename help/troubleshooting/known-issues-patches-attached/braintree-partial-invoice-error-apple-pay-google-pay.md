---
title: 'Adobe Commerce 2.4.4: 부분 송장을 생성할 수 없음'
description: 이 문서에서는 결제 방법으로 Apple Pay 또는 Google Pay through Braintree을 사용할 때 사용자가 부분 송장을 생성할 수 없는 문제에 대한 핫픽스를 제공합니다.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: 부분 송장을 생성할 수 없음

이 문서에서는 결제 방법으로 Apple Pay 또는 Google Pay through Braintree을 사용할 때 사용자가 부분 송장을 생성할 수 없는 문제에 대한 핫픽스를 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 방법) 2.4.4

## 문제

Apple Pay 또는 Google Pay를 결제 방법으로 사용하면 &quot;*&#39;vault_capture&#39; 명령이 없습니다. 명령을 확인하고 다시 시도하십시오.부분 송장을 만드는 동안*&quot;이(가) 발생했습니다.

<u>재현 단계</u>:

1. Adobe Commerce 웹 사이트를 엽니다.
1. 간단한 제품을 장바구니에 추가합니다(수량 2).
1. 장바구니에서 결제 방법으로 **Apple 결제** 또는 **Google 결제**&#x200B;를 선택합니다.
1. 주문하십시오.
1. 백엔드에서 주문 세부 사항을 엽니다.
1. 부분 송장을 생성합니다.
1. 나머지 금액에 대해 다른 송장을 생성합니다.

<u>예상 결과</u>:

부분 송장이 생성됩니다.

<u>실제 결과</u>:

첫 번째 부분 송장이 생성됩니다. 두 번째 부분 청구서를 만드는 동안 다음 오류가 발생합니다. *&#39;vault_capture&#39; 명령이 없습니다. 명령을 확인하고*&#x200B;을(를) 다시 시도하십시오.

## 원인

Adobe Commerce은 일부 송장을 작성하기 위해 자격 증명 모음에 신용 카드 세부 사항을 저장합니다. 현재 Apple Pay 및 Google Pay를 보관하는 기능은 없습니다.

## 솔루션

이 문제를 해결하려면 다음 패치를 적용합니다.

[Braintree_disabled_partial_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## 패치 적용 방법

지침은 [Adobe에서 제공한 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.
