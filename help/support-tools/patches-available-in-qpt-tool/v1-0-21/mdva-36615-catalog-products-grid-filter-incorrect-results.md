---
title: 'MDVA-36615: 카탈로그 제품 표 필터 잘못된 결과'
description: MDVA-36615 패치는 관리 제품 그리드에서 잘못된 제품 카운트와 관련된 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36615입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 7ed70753-c637-4c13-8290-aa5e8a4d1b65
feature: Catalog Management, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36615: 카탈로그 제품 격자 필터가 잘못된 결과

MDVA-36615 패치는 관리 제품 그리드에서 잘못된 제품 카운트와 관련된 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치되었습니다. 패치 ID는 MDVA-36615입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.4.2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 제품 그리드의 잘못된 제품 수입니다.

<u>재현 단계:</u>

1. 이름에 동일한 구(예: &quot;red shirt&quot; / &quot;red shirt xs&quot;)가 있는 간단하고 구성 가능한 제품을 만듭니다.
1. 다음에서 *관리자* 사이드바, 이동 **카탈로그** > **제품** > 이 구를 검색합니다.
1. 클릭 **필터**. 유형 설정 *구성 가능한 제품*.
1. 클릭 **필터 적용**.

<u>실제 결과:</u>

일치하는 제품 카운터의 올바른 번호입니다.

<u>예상 결과:</u>

일치하는 제품 카운터의 숫자가 잘못되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
