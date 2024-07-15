---
title: 'MDVA-37182: Elasticsearch 6과 7에서 검색 결과가 일치하지 않음'
description: MDVA-37182 패치는 Elasticsearch 버전 6 및 7에서 일관되지 않은 검색 동작과 관련된 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37182입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182: Elasticsearch 6과 7에서 검색 결과가 일치하지 않음

MDVA-37182 패치는 Elasticsearch 버전 6 및 7에서 일관되지 않은 검색 동작과 관련된 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37182입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.4.1의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.1-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

일관성 없는 검색 동작.

<u>재현 단계</u>:

1. 다음 세부 정보를 사용하여 제품을 만듭니다.
   * 이름: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKU: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. 검색 엔진을 Elasticsearch 6 (ES6)으로 설정합니다.
1. 전체 색인 재지정을 실행합니다.
1. 상점 앞에서 &quot;5127s&quot;를 검색하세요.
1. 검색 엔진을 Elasticsearch 7 (ES7)로 설정합니다.
1. 전체 색인 재지정을 실행합니다.
1. 상점 앞에서 &quot;5127s&quot;를 검색하세요.

<u>실제 결과:</u>:

ES6: 검색은 결과를 반환하지 않습니다.ES7: 검색은 3개의 제품을 반환합니다.

<u>예상 결과:</u>:

검색은 두 버전 모두에 대해 하나의 제품을 반환합니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
