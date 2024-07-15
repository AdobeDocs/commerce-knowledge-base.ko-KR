---
title: '"Adobe Commerce 2.4.0: "장바구니에 선택 항목 추가"가 작동하지 않음"'
description: 이 문서에서는 고객의 장바구니를 관리할 때 Commerce 관리자의 알려진 버튼 손상 문제에 대한 해결 방법을 제공합니다. 선택한 제품을 고객의 장바구니에 추가하려고 할 때 섹션 하단에 있는 **내 장바구니에 선택 항목 추가** 단추가 작동하지 않습니다. 이 문제는 두 개의 **내 장바구니에 선택 항목 추가** 단추가 있는 관리 패널 페이지에서 발생합니다. Adobe Commerce 2.4.1에서 영구 수정 사항을 사용할 수 있습니다.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;장바구니에 선택 항목 추가&quot;가 작동하지 않음

이 문서에서는 고객의 장바구니를 관리할 때 Commerce 관리자의 알려진 버튼 손상 문제에 대한 해결 방법을 제공합니다. 선택한 제품을 고객의 장바구니에 추가하려고 할 때 섹션 하단에 있는 **선택 항목을 장바구니에 추가** 단추가 작동하지 않습니다. 이 문제는 두 개의 **내 장바구니에 선택 항목 추가** 단추가 포함된 관리 패널 페이지에서 발생합니다. Adobe Commerce 2.4.1에서 영구 수정 사항을 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.0(모든 배포 메서드)

## 문제

<u>재현 단계</u>

1. 두 개의 **선택 항목을 내 장바구니에 추가** 단추가 있는 관리 패널 페이지로 이동합니다.
1. 장바구니에 추가할 항목을 선택하십시오.
1. 섹션 하단에 있는 **선택 항목을 장바구니에 추가** 단추를 클릭합니다.

<u>예상 결과</u>

모든 선택 항목이 예상대로 장바구니에 추가됩니다.

<u>실제 결과</u>

Adobe Commerce이 선택 사항을 내 장바구니에 추가하지 않습니다.

## 솔루션

페이지 상단에 있는 **선택 항목을 장바구니에 추가** 단추가 계속 작동합니다. 이 문제는 4분기 1일 릴리스될 예정인 Adobe Commerce 버전 2.4.1에서 수정될 예정입니다.

## 관련 읽기

* 사용 안내서의 [장바구니 관리](https://docs.magento.com/user-guide/sales/shopping-assisted-cart-manage.html).
* [Adobe Commerce 2.4.0 알려진 문제: 원시 메시지 데이터가 지원 기술 자료의 상점](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)에 표시됩니다.
* [Adobe Commerce 2.4.0 알려진 문제: 지원 기술 자료에서 수출 세율이 작동하지 않습니다](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md).
* [Adobe Commerce 2.4.0 알려진 문제: 지원 기술 자료의 여러 주소 체크아웃](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)에 Braintree 결제 방법이 표시되지 않습니다.
