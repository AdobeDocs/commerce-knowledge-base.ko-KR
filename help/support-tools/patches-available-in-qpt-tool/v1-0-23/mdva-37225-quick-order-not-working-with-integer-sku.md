---
title: 'MDVA-37225: 빠른 주문이 정수 SKU에서 작동하지 않음'
description: Adobe Commerce용 MDVA-37225 품질 패치는 가져온 SKU에 정수 값이 있을 때 빠른 주문을 만들 때 페이지가 로드되지 않는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37225입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225: 빠른 주문이 정수 SKU에서 작동하지 않음

Adobe Commerce용 MDVA-37225 품질 패치는 가져온 SKU에 정수 값이 있을 때 빠른 주문을 만들 때 페이지가 로드되지 않는 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37225입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.4.1-p1의 Adobe Commerce용으로 설계되었습니다
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.1-2.4.2-p1과도 호환됩니다

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소</u>:

B2B 모듈이 설치된 Adobe Commerce

<u>재현 단계</u>:

1. B2B 빠른 주문 기능을 활성화합니다.
1. SKU가 포함된 4개의 간단한 제품을 만드십시오(예: SKU: *00100*, *001E002*, *001E02C* 및 *7100824*).
1. 프론트엔드의 ``<storefront_url>/quickorder`` 페이지로 이동하여 다음 예제 콘텐츠가 포함된 CSV 파일을 사용하여 주문을 만드십시오.

| sku | 수량 |
|---|---|
| 00100 | 1 |


<u>예상 결과</u>:

제품(예: SKU = *00100*&#x200B;인 제품)이 예상대로 장바구니에 추가됩니다.

<u>실제 결과</u>:

페이지가 로드되지 않고 장바구니에 제품이 추가되지 않습니다.


## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 개발자 설명서에서 다음 링크를 사용하십시오.

* Adobe Commerce 및 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html)

## 관련 읽기

지원 기술 자료의 품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 지원 기술 자료에서 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
