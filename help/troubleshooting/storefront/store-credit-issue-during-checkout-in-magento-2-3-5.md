---
title: Adobe Commerce 2.3.5에서 체크아웃 중 크레딧 문제 저장
description: 이 문서에서는 Adobe Commerce 2.3.5에서 체크아웃 중 알려진 스토어 크레딧 관련 문제에 대한 해결 방법을 제공합니다. 이 문제에서는 쇼핑객이 스토어 크레딧 사용을 선택하고 나중에 제거한 후 체크아웃 중에 오류를 받게 됩니다. Adobe Commerce 2.3.6에서 영구 수정 사항을 사용할 수 있습니다.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.3.5에서 체크아웃 중 크레딧 문제 저장

이 문서에서는 Adobe Commerce 2.3.5에서 체크아웃 중 알려진 스토어 크레딧 관련 문제에 대한 해결 방법을 제공합니다. 이 문제에서는 쇼핑객이 스토어 크레딧 사용을 선택하고 나중에 제거한 후 체크아웃 중에 오류를 받게 됩니다. Adobe Commerce 2.3.6에서 영구 수정 사항을 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.3.5
* 클라우드 인프라의 Adobe Commerce 2.3.5

## 문제

<u>재현 단계</u>:

1. 고객이 장바구니에 제품을 추가하고 체크아웃을 진행합니다.
1. 고객이 결제 방법으로 스토어 크레딧을 지정합니다.
1. 고객이 스토어 크레딧을 제거하고 결제 방법을 변경합니다.
1. 고객은 체크아웃을 통해 진행합니다.

<u>예상 결과</u>:

모든 주문 정보가 올바르게 표시됩니다.

<u>실제 결과</u>:

Adobe Commerce에서 주문 페이지의 주문 요약 섹션에 오류가 발생합니다.

## 솔루션

고객은 주문 페이지를 새로 고칠 수 있으며, 주문 요약의 정보가 올바르게 로드됩니다. 수정 사항은 2020년 4분기에 릴리스될 예정인 Adobe Commerce 2.3.6에서 사용할 수 있습니다.

## 관련 읽기

지원 기술 자료의 Adobe Commerce 2.3.5 알려진 문제 문서:

* [Adobe Commerce 2.3.5에서 가상 제품이 올바르게 처리되지 않는 다중 배송 주문](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.5 및 2.3.5-p1의 국가 결제 방법 문제](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)


* [Adobe Commerce 2.3.5의 대량 작업 제품 수 알려진 문제](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Amazon용 패치 Adobe Commerce 2.3.5-p1 의 결제 체크아웃 문제](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Adobe Commerce 2.3.5의 제품 비교 문제](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

개발자 설명서에서:

* [Adobe Commerce 2.3.5 알려진 문제](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
