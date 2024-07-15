---
title: 'Adobe Commerce 2.4.2: Braintree Venmo 결제가 작동하지 않음'
description: 이 문서에서는 체크아웃 중에 Braintree 벤모를 사용할 때 주문이 생성되지 않는 알려진 Adobe Commerce 2.4.2 문제에 대해 설명합니다. 현재 사용할 수 있는 해결 방법이 없습니다.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2: Braintree Venmo 결제가 작동하지 않음

이 문서에서는 체크아웃 중에 Braintree 벤모를 사용할 때 주문이 생성되지 않는 알려진 Adobe Commerce 2.4.2 문제에 대해 설명합니다. 현재 사용할 수 있는 해결 방법이 없습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.4.2

## 문제

<u>사전 조건</u>:

Braintree 구성에서 Venmo 결제를 활성화합니다.

<u>재현 단계</u>:

1. 상점 첫 화면에서 장바구니에 항목을 추가합니다.
1. **체크아웃**&#x200B;을 진행합니다.
1. 적절한 배송 방법을 선택합니다.
1. 결제 방법으로 **Venmo**&#x200B;을(를) 선택하십시오.
1. **Venmo로 결제**&#x200B;를 클릭합니다.
1. **주문**&#x200B;을 클릭하세요.

<u>실제 결과</u>:

고객이 Venmo 앱에서 스토어로 다시 리디렉션되고 오류 메시지가 표시되지 않으면 Adobe Commerce 코드에서 주문이 생성되지 않습니다. Braintree 시 순서가 생성됩니다.

<u>예상 결과</u>:

주문은 고객이 Venmo 앱에서 스토어로 다시 리디렉션된 후 Adobe Commerce에서 생성되며 예상대로 Braintree에서 생성됩니다.

## 솔루션

현재 사용할 수 있는 해결 방법이 없습니다.
