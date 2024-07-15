---
title: 'MDVA-36718: 사용자 지정 옵션은 API 변경 후 유지됩니다.'
description: MDVA-36718 Magento 패치는 API를 통해 변경된 후 이전 사용자 지정 옵션이 남아 있을 때 문제를 해결합니다.
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718: API 변경 후 사용자 지정 옵션이 남음

MDVA-36718 Magento 패치는 API를 통해 변경된 후 이전 사용자 지정 옵션이 남아 있을 때 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-36718입니다. 이 문제는 Magento 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Magento 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. **드롭다운 유형** 사용자 지정 옵션을 추가합니다.
1. API를 통해 사용자 지정 옵션 업데이트: `PUT` 요청을 `/V1/products/options/{optionId}`(으)로 보냅니다.

<u>예상 결과</u>:

사용자 지정 옵션이 예상대로 업데이트됩니다.

<u>실제 결과</u>:

새 사용자 지정 옵션이 추가되지만 이전 사용자 지정 옵션은 유지됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구의 Magento 문제에 대한 패치 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
