---
title: 'Adobe Commerce 2.4.2 B2B: 할인은 결제 방법 변경 사항으로 남음'
description: 이 문서에서는 체크아웃 시 결제 방법을 변경한 후 결제 방법 관련 할인이 지속되는 알려진 Adobe Commerce 2.4.2 B2B 문제에 대해 설명합니다. 현재 사용할 수 있는 해결 방법이 없습니다.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: 할인은 결제 방법 변경 사항으로 남음

이 문서에서는 체크아웃 시 결제 방법을 변경한 후 결제 방법 관련 할인이 지속되는 알려진 Adobe Commerce 2.4.2 B2B 문제에 대해 설명합니다. 현재 사용할 수 있는 해결 방법이 없습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.2
* 클라우드 인프라의 Adobe Commerce 2.4.2
* Adobe Commerce 1.3.1용 B2B


## 문제

<u>재현 단계</u>:

1. 결제 방법에 연결된 장바구니 **가격 규칙**&#x200B;을(를) 만듭니다(예: Paypal 사용자는 20% 할인을 받습니다).
1. PO(구매 주문)를 생성하고 결제 방법으로 Paypal을 선택합니다. 할인이 적용됩니다
1. PO가 승인되었습니다.
1. 결제 페이지로 이동하여 주문을 완료합니다.
1. 다른 결제 방법을 선택하십시오.

<u>실제 결과</u>:

결제 방법 할인이 주문 총액에 적용된 상태로 유지됩니다.  오류 메시지가 표시되지 않습니다. 스토어 소유자는 주문 내역을 확인하여 이 오류를 확인할 수 있습니다.

<u>예상 결과</u>: 예상대로 결제 방법 할인이 주문 합계에서 제거됩니다.

## 솔루션

현재 사용할 수 있는 해결 방법이 없습니다.
