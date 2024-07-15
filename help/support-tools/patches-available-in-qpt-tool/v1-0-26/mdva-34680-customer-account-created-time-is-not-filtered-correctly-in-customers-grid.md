---
title: "MDVA-34680: 고객 계정이 고객의 그리드에서 올바르게 필터링되지 않음"
description: MDVA-34680 패치는 00:00 UTC 이후에 만든 고객 계정이 고객 그리드에서 올바르게 필터링되지 않을 때 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-34680입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680: 고객 계정이 고객 그리드에서 올바르게 필터링되지 않음

MDVA-34680 패치는 00:00 UTC 이후에 만든 고객 계정이 고객 그리드에서 올바르게 필터링되지 않을 때 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-34680입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라 2.4.1 및 2.4.2의 Adobe Commerce

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.6-2.3.7 및 2.4.1-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

00:00 UTC 이후에 고객 계정이 만들어지고 해당 날짜까지 계정을 필터링하려고 하면 이 고객이 반환되지 않습니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **일반**(으)로 이동하여 시간대를 동부 표준 [미국/뉴욕]으로 설정합니다.
1. 00:00 UTC 이후에 새 고객 계정을 만듭니다.
1. **고객** > **모든 고객**(으)로 이동하여 오늘 날짜까지 계정을 필터링하세요.

<u>예상 결과</u>:

고객 계정 필터는 00:00 UTC 이후 오늘 생성된 새 계정을 보여 줍니다.

<u>실제 결과</u>:

고객 계정 필터에 오늘 생성된 새 계정이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
