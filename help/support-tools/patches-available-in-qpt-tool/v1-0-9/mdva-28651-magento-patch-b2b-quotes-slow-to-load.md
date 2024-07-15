---
title: 'MDVA-28651: B2B - 따옴표가 느리게 로드됨'
description: MDVA-28651 패치는 따옴표 로드 시 여러 성능 문제가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 수정되었습니다.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651: B2B - 따옴표가 느리게 로드됨

MDVA-28651 패치는 따옴표 로드 시 여러 성능 문제가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 수정되었습니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.4의 Adobe Commerce용으로 설계되었습니다.
* 이 패치는 Adobe Commerce 버전(Adobe Commerce 온프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.3.5-p1, 2.4.0 및 2.4.1)과도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 견적 목록 페이지의 성능 문제:

* 견적 목록의 이중 로드: 먼저 전체 페이지를 포함하고, 두 번째는 Ajax 요청에 의해 수행됩니다.
* 플러그인에서 각 인용 부호를 로드하는 루프.
* 견적이 스냅샷으로 변환될 때 견적 항목의 이중 로드.

<u>재현 단계</u>

1. 고객에게 40개 이상의 견적이 할당되어 있습니다.
1. **내 따옴표** 페이지에 로그인하고 탐색합니다.

<u>실제 결과</u>

**내 따옴표** 페이지의 콘텐츠(페이지 로드 + 그리드에 표시된 데이터)를 완전히 로드하는 데 걸리는 응답 시간은 ~ 45초입니다.

<u>예상 결과</u>

**내 견적** 페이지의 콘텐츠를 완전히 로드하는 응답 시간은 45초 미만이어야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
