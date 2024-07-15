---
title: 'Adobe Commerce 2.4.0: 다중 배송 체크아웃에서 보상 포인트를 제거하는 동안 404 오류 발생'
description: 이 문서에서는 다중 배송 체크아웃 페이지에서 보상 포인트를 제거할 때 "*404 찾을 수 없음*" 웹 페이지 오류에 대한 Adobe Commerce 2.4.0의 알려진 문제에 대한 해결 방법을 제공합니다. 현재 다중 배송 체크아웃 페이지에서 주문 결제에 사용된 보상 포인트를 제거하려고 하면 보상 포인트 취소 성공 대신 "*404 찾을 수 없음*" 페이지가 표시됩니다. 이 문제는 Adobe Commerce 2.4.1 패치 릴리스에서 해결됩니다.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: 다중 배송 체크아웃 시 보상 포인트를 제거하는 도중 404 오류 발생

이 문서에서는 다중 배송 체크아웃 페이지에서 보상 포인트를 제거할 때 &quot;*404 찾을 수 없음*&quot; 웹 페이지 오류에 대한 Adobe Commerce 2.4.0의 알려진 문제에 대한 해결 방법을 제공합니다. 현재 다중 배송 체크아웃 페이지에서 주문 결제에 사용된 보상 포인트를 제거하려고 하면 보상 포인트를 취소하는 대신 &quot;*404 찾을 수 없음*&quot; 페이지가 표시됩니다. 이 문제는 Adobe Commerce 2.4.1 패치 릴리스에서 해결됩니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.0(모든 배포 메서드)

## 문제

<u>재현 단계</u>

1. 상점으로 이동하여 고객으로 로그인합니다.
1. **장바구니**&#x200B;에 제품을 두 개 이상 추가하십시오.
1. **미니 장바구니**&#x200B;를 엽니다.
1. **장바구니 보기 및 편집** 링크를 클릭합니다.
1. **여러 주소로 체크 아웃** 링크를 클릭합니다.
1. **여러 주소로 배송** 페이지에서 배송 주소를 선택하십시오.
1. **배송 정보로 이동** 단추를 클릭합니다.
1. 각 주소에 대해 **정액 요금 - 고정 배송 방법**&#x200B;을 선택하세요.
1. **청구 정보 계속** 단추를 클릭합니다.
1. **청구 정보** 페이지에서 **보상 포인트 사용** 확인란을 선택하세요.
1. **주문 검토로 이동** 단추를 클릭합니다.
1. 보상 포인트를 제거하려면 주소에 대한 **제거** 링크를 클릭하십시오.

<u>예상 결과</u>

* **장바구니** 페이지가 표시됩니다.
* &quot;*이(가) 이 주문에서 보상 포인트를 제거했습니다.*&quot; 메시지가 표시되어야 합니다.

<u>실제 결과</u>

&quot;*404 찾을 수 없음*&quot; 오류 페이지가 나타납니다.

## 해결 방법

해결 방법은 구매자가 **장바구니**(으)로 돌아가서 **장바구니** 웹 페이지에서 보상 포인트를 제거하는 것입니다. 이 문제는 2020년 4분기에 릴리스될 예정인 Adobe Commerce 버전 2.4.1 패치에서 수정될 예정입니다.

## 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
