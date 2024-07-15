---
title: 고급 검색 페이지의 MDVA-28357 SKU 검색이 작동하지 않음
description: MDVA-28357은 고급 검색 페이지에서 제품 SKU로 검색해도 검색 결과에 관련 제품이 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.1에서 해결되었습니다.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 고급 검색 페이지의 MDVA-28357 SKU 검색이 작동하지 않음

MDVA-28357은 고급 검색 페이지에서 제품 SKU로 검색해도 검색 결과에 관련 제품이 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.1에서 해결되었습니다.

## 영향을 받는 제품 및 버전

* 이 패치는 Adobe Commerce 온-프레미스 2.3.4-p2용으로 설계되었습니다.
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라 2.3.0 - 2.3.5-p2 및 2.4.0 - 2.4.0-p1과도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고급 검색에서 SKU를 사용하여 검색은 와일드카드를 사용하여 SKU 필드를 쿼리합니다. 와일드카드는 `sku.keyword`에만 사용할 수 있으므로 예상한 제품을 반환하지 않습니다.

<u>재현 단계</u>

1. 고급 검색 페이지로 이동합니다.
1. SKU 번호로 검색합니다.

<u>실제 결과</u>

오류 메시지가 표시됩니다. *이 검색 조건과 일치하는 항목을 찾을 수 없습니다. 검색*&#x200B;을(를) 수정합니다.

<u>예상 결과</u>

다음 검색 조건을 사용하여 *1개 항목을 찾았습니다.* *SKU: XX-XXXX*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: 개발자 설명서에서 [품질 패치 도구를 사용하여 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
