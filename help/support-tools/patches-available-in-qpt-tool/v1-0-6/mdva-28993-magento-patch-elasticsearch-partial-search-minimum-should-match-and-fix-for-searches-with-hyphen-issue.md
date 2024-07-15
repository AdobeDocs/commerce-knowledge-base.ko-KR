---
title: '"MDVA-28993: Elasticsearch 부분 검색, "최소값은 일치해야" "하이픈이 있는 검색" 문제 해결"'
description: MDVA-28993 패치는 Elasticsearch 엔진에 대한 "최소값은 일치해야 함" 기능과 부분 검색을 구현하고 검색 쿼리에서 하이픈 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6이 설치된 경우 사용할 수 있습니다.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993: Elasticsearch 부분 검색, &quot;최소값은 일치해야 함&quot; 및 &quot;하이픈이 있는 검색&quot; 문제 해결

MDVA-28993 패치는 Elasticsearch 엔진에 대한 &quot;최소값은 일치해야 함&quot; 기능과 부분 검색을 구현하고 검색 쿼리에서 하이픈 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.3.4의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스/Adobe Commerce on cloud infrastructure 2.3.4-2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.


## 문제

하이픈(-)이 포함된 SKU를 검색하기 위해 Elasticsearch 6을 사용하는 경우 검색 결과가 너무 많이 반환됩니다.

<u>재현 단계:</u>

1. 가게 앞쪽으로 가보세요

1. 검색 막대에서 하이픈을 포함하는 문자열을 입력합니다(예: &quot;WS-M-Blue&quot;).

<u>예상 결과:</u>

WS-M-Blue만 반환합니다.

<u>실제 결과:</u>

&quot;WS&quot;로 시작하는 모든 SKU를 반환합니다.

## 패치 세부 정보

MDVA-28993 패치에는 다음과 같은 수정 사항과 개선 사항이 포함되어 있습니다.

* 는 Elasticsearch 엔진에 대한 새로운 &quot;일치해야 하는 최소&quot; 기능과 부분 검색을 구현합니다. 구성 세부 정보는 사용 안내서에서 [카탈로그 검색 구성](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match)을 참조하세요.
* Elasticsearch 부분 검색
* 위에서 설명한 &quot;하이픈으로 검색&quot; 문제를 수정합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
