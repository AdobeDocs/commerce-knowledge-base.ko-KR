---
title: "MDVA-28202 패치: 재고 부족 제품이 제대로 필터링되지 않음"
description: MDVA-28202 패치는 Adobe Commerce 스토어 프론트엔드에서 **Price** 필터를 사용하여 재고 부족 제품이 제대로 필터링되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6이 설치된 경우 사용할 수 있습니다.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-28202 패치: 재고 부족 제품이 제대로 필터링되지 않음

MDVA-28202 패치는 Adobe Commerce 스토어 프론트엔드에서 **가격** 필터를 사용하여 재고 부족 제품이 제대로 필터링되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.5-p1의 Adobe Commerce용으로 설계되었습니다.
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.4 - 2.4.1과도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

재고 부족 제품이 Commerce 관리자의 **가격** 필터를 사용하여 제대로 필터링되지 않습니다.

<u>필수 구성 요소:</u>

* **스토어 > 구성 > 카탈로그 > 재고 > 재고 옵션**&#x200B;에서 **재고 부족 제품 표시** = &quot;*예*&quot;를 설정하십시오.

<u>재현 단계:</u>

1. 두 개의 간단한 제품으로 구성 가능한 제품을 만듭니다(예: 설정 **가격** = *$1500*).
1. 구성 가능한 제품을 만드는 동안 두 간단한 제품 모두 &quot;품절&quot;되어야 합니다.
1. 이 구성 가능한 제품을 범주에 할당합니다.
1. 위에서 구성 가능한 제품의 엔터티 ID를 사용하여 `catalog_product_index_price` 테이블을 다시 인덱싱하고 확인하십시오.
1. 모든 제품 가격 = *$0*&#x200B;을(를) 저장합니다.
1. 범주를 로드하고 제품의 가용성을 확인합니다.
1. 계층화된 탐색에서 **가격** 필터를 엽니다.
1. **가격** 필터에 &quot; *$0.00 - $9.99* &quot; 옵션이 있습니다.
1. 위의 **가격** 필터 옵션을 클릭하고 **가격** = *$1500*&#x200B;을(를) 설정하면 위에서 만든 구성 가능한 제품이 제공됩니다.

<u>예상 결과:</u>

이 제품은 예상대로 올바른 가격 범위에서 필터링됩니다.

<u>실제 결과:</u>

제품이 잘못된 가격대 필터에 속합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: 개발자 설명서에서 [품질 패치 도구를 사용하여 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.

구성 가능한 제품에 대한 자세한 내용은 개발자 설명서에서 다음 문서를 참조하십시오. 개발자 설명서에서 [구성 가능한 제품 튜토리얼 만들기](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html).
