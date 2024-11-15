---
title: 'Adobe Commerce 2.3.5 알려진 문제: 가상 제품 다중 배송 주문'
description: 이 문서에서는 가상 제품이 포함된 다중 배송 주문이 올바르게 처리되지 않는 Adobe Commerce 2.3.5의 알려진 문제에 대해 설명합니다.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '202'
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

지원 기술 자료에서:

* [Adobe Commerce 2.3.5의 제품 비교 알려진 문제](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5의 대량 작업 제품 수 알려진 문제](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Amazon용 패치 Adobe Commerce 2.3.5-p1 의 결제 체크아웃 문제](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

개발자 설명서에서:

* [Adobe Commerce 2.3.5 릴리스 노트](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
