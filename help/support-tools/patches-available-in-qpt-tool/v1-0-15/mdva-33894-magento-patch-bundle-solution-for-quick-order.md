---
title: 'MDVA-33894 패치: 빠른 주문을 위한 번들 솔루션'
description: MDVA-33894 패치는 여러 제품 추가 및 제거, SKU 대소문자 구분 등 빠른 주문 기능에 대한 여러 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-33894 패치: 빠른 주문을 위한 번들 솔루션

MDVA-33894 패치는 여러 제품 추가 및 제거, SKU 대소문자 구분 등 빠른 주문 기능에 대한 여러 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 생성되었습니다.** 클라우드 인프라 2.4.0의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.4.0-2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

MDVA-33894 패치는 다음 문제에 대한 수정 사항이 있는 번들 솔루션입니다.

* **내 계정** > **SKU별 주문** 기능은 대소문자를 구분합니다. 유효한 SKU를 입력했지만 대소문자가 올바르지 않은 경우(소문자 등이 아닌 대문자) Adobe Commerce에서 오류가 발생합니다.
* 쇼핑객이 빠른 주문을 사용하여 장바구니에 여러 제품을 추가한 후 제품을 제거하려고 해도 제품이 제거되지 않습니다.
* 일괄 주문에 여러 SKU를 추가할 때 대소문자 구분 문제가 발생합니다.
* 이전에 입력한 SKU의 빠른 주문 페이지 캐시 문제입니다.
* 빠른 주문 수량은 장바구니에 반영되지 않습니다.
* SKU 복제가 제대로 확인되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
