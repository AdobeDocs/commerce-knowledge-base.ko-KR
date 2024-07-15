---
title: Adobe Commerce은 고객에게 잘못된 링크에 로그인하라는 메시지를 표시합니다.
description: 이 문서에서는 알려진 Adobe Commerce 2.3.5 문제에 대한 패치에 대한 링크를 제공합니다. 이 문제에서는 고객에게 로그인하라는 메시지가 표시되지만 확인 이메일을 다시 전송하는 링크가 작동하지 않습니다.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce은 고객에게 잘못된 링크에 로그인하라는 메시지를 표시합니다.

이 문서에서는 알려진 Adobe Commerce 2.3.5 문제에 대한 패치에 대한 링크를 제공합니다. 이 문제에서는 고객에게 로그인하라는 메시지가 표시되지만 확인 이메일을 다시 전송하는 링크가 작동하지 않습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.3.5

## 문제

Adobe Commerce은 다음 메시지를 표시하여 로그인하라는 메시지를 표시합니다. *&quot;이 계정은 확인되지 않습니다. 확인 전자 메일 &quot;*&quot;을(를) 다시 보내려면 여기를 클릭하세요. **여기를 클릭** 링크를 클릭하면 확인 링크 보내기 페이지가 열리지만 비활성 상태입니다.

## 솔루션

이 문제에 대한 패치는 Adobe Commerce 기술 리소스에서 사용할 수 있습니다. [Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368)에 대한 계정 확인 이메일 링크 문제 패치 다시 보내기. 영구 수정 사항은 2020년 4분기에 릴리스될 예정인 Adobe Commerce 2.3.6에서 사용할 수 있습니다.

작성기 패치 적용 방법에 대한 지침은 [Adobe에서 제공하는 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 관련 읽기

Adobe Commerce 2.3.5의 알려진 문제에 대한 지원 기술 자료 및 개발자 설명서 의 문서:

* [Adobe Commerce 2.3.5 알려진 문제: 가상 제품 멀티배송 주문](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Adobe Commerce 2.3.5의 제품 비교 알려진 문제](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5, 2.3.5-p1 패치: 국가 결제 문제](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce은 고객에게 잘못된 링크에 로그인하라는 메시지를 표시합니다.](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Adobe Commerce 2.3.5의 대량 작업 제품 수 알려진 문제](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Amazon용 패치 Adobe Commerce 2.3.5-p1 의 결제 체크아웃 문제](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Adobe Commerce 2.3.5 알려진 문제](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
