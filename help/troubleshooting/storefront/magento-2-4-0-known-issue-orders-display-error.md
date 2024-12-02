---
title: 'Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류'
description: 이 문서에서는 주문 표시 오류에 대한 Adobe Commerce의 알려진 문제에 대한 해결 방법을 제공합니다. 로그인한 고객이 **내 계정** 메뉴(**내 계정 &gt; 내 주문**)에서 주문을 검토할 때 주문 그리드는 11개의 주문이 있는 경우 페이지당 주문 수를 2페이지에서 20개로 전환할 수 없습니다. 또한 페이지당 표시하도록 구성된 주문보다 많은 주문이 있는 경우 주문이 있는 마지막 페이지로 이동할 때 페이지당 표시되는 주문 수를 변경하면 다음과 같은 오류 메시지가 생성됩니다. *주문이 없습니다*. 이 문제는 Adobe Commerce 2.4.1에서 해결됩니다.
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류

이 문서에서는 주문 표시 오류에 대한 Adobe Commerce의 알려진 문제에 대한 해결 방법을 제공합니다. 로그인한 고객이 **내 계정** 메뉴(**내 계정 > 내 주문**)에서 주문을 검토할 때 11개의 주문이 있는 경우 주문 그리드에서 페이지당 주문 수를 2페이지에서 20개로 전환할 수 없습니다. 또한 페이지당 표시하도록 구성된 주문보다 많은 주문이 있는 경우 주문과 함께 마지막 페이지로 이동하면 페이지당 표시되는 주문 수를 변경하면 다음과 같은 오류 메시지가 나타납니다. *주문이 없습니다*. 이 문제는 Adobe Commerce 2.4.1에서 해결됩니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>필수 구성 요소</u>

* Adobe Commerce 2.4.0이 설치되어 있습니다.
* 하나 이상의 카테고리와 하나의 간단한 제품을 만듭니다.

<u>재현 단계</u>

1. 제품으로 11개의 주문을 생성합니다.
1. **내 계정**(으)로 이동합니다.
1. **내 주문**(으)로 이동합니다.
1. 두 번째 페이지를 클릭하여 주문 그리드에 11번째 순서를 표시합니다.
1. 드롭다운 메뉴에서 **페이지당 표시 = 20**&#x200B;을(를) 선택합니다.

<u>예상 결과</u>

예상대로 11개의 주문이 모두 첫 페이지에 표시됩니다.

<u>실제 결과</u>

*주문을 하지 않았습니다* 오류 메시지가 표시됩니다.

## 해결 방법

해결 방법은 구매자가 **내 주문** 페이지를 다시 열도록 하는 것입니다. 그러면 주문 목록이 올바르게 표시됩니다. 이 문제는 2020년 4분기에 릴리스될 예정인 다음 릴리스인 Adobe Commerce 2.4.1에서 수정될 예정입니다.

## 지원 기술 자료의 관련 자료

* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
