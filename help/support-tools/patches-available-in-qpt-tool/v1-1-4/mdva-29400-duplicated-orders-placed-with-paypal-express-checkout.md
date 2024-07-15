---
title: 'MDVA-29400: PayPal Express 체크아웃과 함께 주문된 중복 주문'
description: MDVA-29400 패치는 고객이 PayPal Express Checkout으로 주문을 할 때 중복 주문이 생성되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-29400입니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: PayPal Express 체크아웃 시 중복 주문

MDVA-29400 패치는 고객이 PayPal Express Checkout으로 주문을 할 때 중복 주문이 생성되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-29400입니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 PayPal Express Checkout으로 주문을 하면 중복 주문이 생성됩니다.

<u>필수 구성 요소</u>:

PayPal Express 체크아웃을 활성화하고 구성했습니다.

<u>재현 단계</u>:

1. 장바구니에 제품을 추가합니다.
1. 체크아웃 페이지로 이동하여 결제 방법으로 PayPal Express를 사용합니다.
1. paypal/express/review/ 페이지로 리디렉션됩니다.
1. 주문. 성공 페이지로 리디렉션됩니다.
1. PayPal/express/review/ 페이지로 돌아갑니다.
1. **주문** 단추를 클릭합니다.

<u>예상 결과</u>:

주문은 하나만 생성됩니다.

<u>실제 결과</u>:

다음 오류가 발생했습니다. *PayPal Express 체크아웃 토큰이 존재하지 않습니다* 그러나 두 번째 주문이 완료되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
