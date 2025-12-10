---
title: 'Adobe Commerce 2.3.5 알려진 문제: 가상 제품 멀티배송 주문'
description: 이 문서에서는 가상 제품이 포함된 다중 배송 주문이 올바르게 처리되지 않는 Adobe Commerce 2.3.5의 알려진 문제에 대해 설명합니다.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 39e61a3fe8b75fb613819d89c7d47acdf1c384f6
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Adobe Commerce 2.3.5 알려진 문제: 가상 제품 멀티배송 주문

이 문서에서는 가상 제품이 포함된 다중 배송 주문이 올바르게 처리되지 않는 Adobe Commerce 2.3.5의 알려진 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.3.5
* 클라우드 인프라의 Adobe Commerce 2.3.5

## 문제

<u>재현 단계</u>:

1. 상점 첫 화면에서 실제 및 가상 제품을 장바구니에 추가합니다.
1. 체크아웃을 계속 진행하고 **여러 주소로 체크 아웃**&#x200B;을 선택합니다.
1. 필요한 모든 정보를 추가하고 주문합니다.

<u>예상 결과</u>:

모든 제품에 대한 주문이 완료되었습니다.

<u>실제 결과</u>:

가상 제품에 대한 주문이 비어 있습니다.

## 수정

수정 사항은 2020년 4분기에 릴리스될 예정인 Adobe Commerce 2.3.6에서 사용할 수 있습니다.

## 관련 읽기

개발자 설명서에서:

* [Adobe Commerce 2.3.5 릴리스 노트](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
