---
title: 'MDVA-40101: 상품은 주문 배치 후 미니 장바구니로 남음 PayPal Express Checkout'
description: MDVA-40101 패치는 PayPal Express Checkout을 사용하여 주문을 성공적으로 배치한 후 미니 장바구니에서 항목이 제거되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40101입니다. 이 문제는 Adobe Commerce 2.4.0에서 해결되었습니다.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101: 주문 배치 PayPal Express Checkout 후 항목이 미니 장바구니로 남음

MDVA-40101 패치는 PayPal Express Checkout을 사용하여 주문을 성공적으로 배치한 후 미니 장바구니에서 항목이 제거되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4가 설치되었습니다. 패치 ID는 MDVA-40101입니다. 이 문제는 Adobe Commerce 2.4.0에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

Adobe Commerce(모든 배포 방법) 2.3.7

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

PayPal Express Checkout을 사용하여 주문을 성공적으로 배치한 후에도 항목은 미니 장바구니에 남아 있습니다.

<u>재현 단계</u>:

브라우저의 시크릿 모드에서 PayPal Express Checkout을 사용하여 주문합니다.

<u>예상 결과</u>:

미니 장바구니는 주문이 성공적으로 완료되면 비어 있어야 합니다.

<u>실제 결과</u>:

* 성공 페이지에 빈 미니 장바구니가 표시됩니다.
* 다른 모든 페이지에는 구매한 항목이 있는 미니 장바구니가 표시됩니다.
* 장바구니 링크를 클릭하면 빈 장바구니 페이지로 리디렉션됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
