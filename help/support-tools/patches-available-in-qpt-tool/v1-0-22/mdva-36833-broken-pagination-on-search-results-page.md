---
title: 'MDVA-36833: 검색 결과 페이지에서 끊어진 페이지 매김'
description: MDVA-36833 패치는 공유 카탈로그가 활성화되고 일부 제품이 공유 카탈로그에서 제외된 경우 페이지 매김이 중단되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36833입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833: 검색 결과 페이지에서 끊어진 페이지 매김

MDVA-36833 패치는 공유 카탈로그가 활성화되고 일부 제품이 공유 카탈로그에서 제외된 경우 페이지 매김이 중단되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-36833입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** Adobe Commerce(모든 배포 방법) 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

공유 카탈로그에서 일부 제품을 제외하면 검색 결과에 대한 페이지 매김이 손상됩니다.

<u>재현 단계:</u>

1. 공유 카탈로그를 활성화합니다.
1. **카탈로그** > **공유 카탈로그**(으)로 이동한 다음 모든 제품을 할당하여 기본 공유 카탈로그를 설정하십시오.
1. 가게 앞에 짐을 싣고 &quot;재킷&quot;을 찾아보세요.
1. 첫 페이지에 나열된 제품을 확인합니다. 12개의 제품이 있어야 합니다.
1. 첫 번째 페이지에서 11개의 SKU를 적어 두십시오. 백엔드로 이동하여 기본 공유 카탈로그를 로드합니다.
1. 이전에 언급된 SKU를 기본 공유 카탈로그에서 할당 해제합니다.
1. 가게 앞에 가서 &quot;재킷&quot;을 찾아보세요.
1. 검색 결과의 첫 페이지를 확인합니다.

<u>실제 결과:</u>

첫 번째 페이지에는 하나의 제품이 있고 나머지 제품은 두 번째 페이지에서 사용할 수 있습니다.

<u>예상 결과:</u>

첫 페이지에는 12개의 제품이 있어야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).


## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
