---
title: "MDVA-32545 패치: 주문 송장이 자동으로 전송되지 않음"
description: MDVA-32545 패치는 관리자가 보낸 주문에 대해 송장 전자 메일이 고객에게 자동으로 전송되지 않는 문제를 해결합니다. 이는 **Braintree** 또는 **PayPal Payflow Pro**와 같은 **Sale** 거래 유형의 결제 방법에 영향을 줍니다.
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-32545 패치: 주문 송장이 자동으로 전송되지 않음

MDVA-32545 패치는 관리자가 보낸 주문에 대해 송장 전자 메일이 고객에게 자동으로 전송되지 않는 문제를 해결합니다. **Braintree** 또는 **PayPal Payflow Pro**&#x200B;와 같은 **Sale** 거래 유형의 결제 방법에 영향을 줍니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.2-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. **Sale** 거래 유형의 결제 방법을 사용하도록 설정합니다. (예: **Braintree** 또는 **PayPal Payflow Pro**)
1. 간단한 제품을 만듭니다.
1. 프론트엔드에 고객 계정을 만듭니다.
1. 책임자로부터 주문을 합니다.

<u>예상 결과</u>:

송장 이메일은 예상대로 고객에게 자동으로 전송됩니다.

<u>실제 결과</u>:

송장 이메일은 고객에게 자동으로 전송되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
