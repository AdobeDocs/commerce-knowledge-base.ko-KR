---
title: 'MDVA-37874: 고정 할인이 전체 장바구니에 적용되지 않음'
description: MDVA-37874 패치는 전체 장바구니에 대한 **고정 할인 금액**이 두 개 이상의 옵션이 포함된 번들 제품에 잘못 적용되는 경우 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37874입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874: 고정 할인이 전체 장바구니에 적용되지 않음

MDVA-37874 패치는 전체 장바구니에 대한 **고정 할인 금액**&#x200B;이 두 개 이상의 옵션이 포함된 번들 제품에 잘못 적용되는 경우 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37874입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.4.2의 Adobe Commerce용으로 설계되었습니다
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.6-2.3.7 및 2.4.1-2.4.2-p1과도 호환됩니다

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제


<u>재현 단계</u>:

1. 전체 장바구니에 대해 **고정 할인 금액**&#x200B;이 포함된 장바구니 규칙을 만듭니다.
1. 번들 제품을 장바구니에 추가합니다(번들 제품에는 선택한 몇 가지 옵션이 포함되어야 함).
1. 장바구니 페이지로 이동하여 할인을 확인합니다.


<u>예상 결과</u>:

고정 할인 금액은 예상대로 전체 장바구니에 적용됩니다.

<u>실제 결과</u>:

고정 할인 금액은 장바구니의 일부에만 적용됩니다.


## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
