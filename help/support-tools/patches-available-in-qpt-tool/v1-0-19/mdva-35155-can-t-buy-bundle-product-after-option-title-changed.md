---
title: "MDVA-35155: 옵션 제목이 변경된 후에 번들 제품을 구입할 수 없음"
description: MDVA-35155 패치는 옵션 제목을 변경한 후 번들 제품을 구입할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-35155입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155: 옵션 제목이 변경된 후에는 번들 제품을 구입할 수 없음

MDVA-35155 패치는 옵션 제목을 변경한 후 번들 제품을 구입할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-35155입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

옵션 제목을 변경한 후에는 번들 제품을 구입할 수 없습니다.

<u>재현 단계</u>:

1. **제품 가져오기**&#x200B;를 통해 새 번들 제품을 만드십시오.
1. 이 제품은 관리자 및 프론트엔드 모두에서 정상적인 상태입니다(재고 상태이며 장바구니에 추가할 수 있음).
1. `bundle_values`에서 이름이 변경된 동일한 제품을 업데이트한 다음 제품을 다시 가져오십시오.

<u>예상 결과</u>:

기존 번들 옵션이 새 이름으로 업데이트되고 동일한 항목을 유지합니다.

<u>실제 결과</u>:

* 관리자가 동일한 SKU를 사용하는 제품을 단일 번들 옵션 섹션에 병합하려고 하므로 옵션 섹션이 비어 있습니다.
* 이 제품은 프런트 엔드에서 품절되었습니다(색인 재지정 후에도).

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
