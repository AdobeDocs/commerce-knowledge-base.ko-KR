---
title: 'MDVA-43232: 시각적 머천다이저의 제품을 특별 가격에서 상단(또는 하단)으로 정렬하면 오류가 발생합니다.'
description: MDVA-43232 패치는 시각적 머천다이저에서 범주를 저장하는 동안 특수 가격을 최상위(또는 최하위)로 정렬하는 경우 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43232입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232: 시각적 머천다이저의 제품을 특별 가격에서 상단(또는 하단)으로 정렬하면 오류가 발생합니다.

MDVA-43232 패치는 시각적 머천다이저에서 범주를 저장하는 동안 특수 가격을 최상위(또는 최하위)로 정렬하는 경우 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43232입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

시각적 머천다이저의 제품을 특별 가격에서 상위(또는 하위)로 정렬하면 범주를 저장하는 동안 오류가 발생합니다.

<u>재현 단계</u>:

1. 웹 사이트가 두 개인지 확인하십시오.
1. **스토어** > **구성** > **카탈로그** > **가격**(으)로 이동하여 카탈로그 가격 범위 = 웹 사이트를 설정합니다.
1. 다시 **스토어** > **구성** > **카탈로그** > **시각적 머천다이저** > **범주 규칙에 대한 표시 특성** >(으)로 이동하고 특별 가격을 추가합니다.
1. 간단한 제품을 만들고 두 웹 사이트에 제품을 할당합니다.
1. 제품의 기본 범위에 특별 가격을 추가합니다.
1. 다른 상점의 범위로 전환하고 해당 제품의 가격과 특별 가격을 모두 무시합니다.
1. `catalog_product_price`을(를) 다시 인덱싱합니다.
1. **카탈로그** > **범주**(으)로 이동하여 새 범주를 만드십시오.
1. 특별 가격이 있는 제품을 필터링할 카테고리 규칙을 추가합니다.
1. 범주를 저장합니다.
1. 범주 내 제품 섹션에서 정렬 순서 = 특별 가격을 최상위(또는 최하위)로 설정합니다.
1. 범주를 다시 저장합니다.

<u>예상 결과</u>:

범주가 오류 없이 저장됩니다.

<u>실제 결과</u>:

예외가 throw되었습니다.

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
