---
title: 'MDVA-33453: 페이지 빌더 미리보기가 사이트 간 제품 가격 차이를 할인'
description: MDVA-33453 패치는 일치하는 제품에 각 웹 사이트의 가격이 다른 경우 페이지 빌더 미리보기가 중단되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453: 페이지 빌더 미리 보기는 사이트마다 제품 가격을 다르게 합니다.

MDVA-33453 패치는 일치하는 제품에 각 웹 사이트의 가격이 다른 경우 페이지 빌더 미리보기가 중단되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.4.1의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.6 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다양한 웹 사이트에서 가격이 다른 제품이 있을 경우 페이지 빌더 제품 미리보기가 중단됩니다.

<u>재현 단계</u>:

1. Commerce 관리 패널에 로그인합니다.
1. 두 개의 웹 사이트를 만듭니다.
1. 간단한 제품을 만듭니다.
1. 각 웹 사이트에서 제품에 대한 다른 가격을 설정합니다.
1. cron 을 실행하고 색인을 다시 지정합니다.
1. CMS 페이지를 만들거나 편집하고 제품 블록을 사용하여 제품을 추가합니다.

<u>실제 결과</u>:<br>

다음 오류가 발생합니다.

*템플릿 필터링 오류: ID가 &quot;2&quot;인 항목(Magento\\Catalog\\Model\\Product\\Interceptor)이 이미 있습니다.*

<u>예상 결과</u>:<br>

오류가 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
