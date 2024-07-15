---
title: 'MDVA-30963: 관리 제품 검색 필터가 예상대로 작동하지 않음'
description: MDVA-30963 패치는 Commerce 관리자 및 제품 검색 필터가 예상대로 작동하지 않는 문제를 해결합니다. 저장소 보기 범위에서 재정의된 값은 **모든 저장소 보기** 저장소 보기 범위에서 필터링할 때도 고려됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963: 관리 제품 검색 필터가 예상대로 작동하지 않음

MDVA-30963 패치는 Commerce 관리자 및 제품 검색 필터가 예상대로 작동하지 않는 문제를 해결합니다. 저장소 보기 범위에서 재정의된 값은 **모든 저장소 보기** 저장소 보기 범위에서 필터링할 때도 고려됩니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.0

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. **스토어** > **구성** > **카탈로그** > **카탈로그** > **가격** > **카탈로그 가격 범위** = *웹 사이트*&#x200B;를 설정합니다.
1. 두 개의 서로 다른 통화가 포함된 웹 사이트를 만듭니다(예: 기본 웹 사이트는 인도 스토어 \[Rupee ₹\]이고 두 번째 웹 사이트는 미국 스토어 \[Dollar $\])입니다).
1. 다음 **기본 통화**, **기본 표시 통화** 및 **허용되는 통화**&#x200B;를 설정하십시오.
   * **기본 구성** = *미국 달러(기본값)*
   * **기본 웹 사이트** = *인도 루피*
   * **WebsiteUS** = **기본값 사용** = *미국 달러*
1. **스토어** > **환율** = *1:1*&#x200B;을 설정합니다.
1. 다음 가격으로 두 웹 사이트에 할당된 테스트 간단한 제품을 만듭니다.
   * **기본 가격** = **미국 웹 사이트 가격** = *123 USD*
   * **기본 웹 사이트 가격** = *321 루피*
1. 미국 스토어에만 액세스할 수 있는 하위 관리자 사용자를 만듭니다.
1. 미국 상점으로 이동하여 장바구니에 제품을 담으십시오(예: *123 USD 가격*).
1. 방금 만든 subAdmin으로 관리자에 로그인합니다(예: *미국 전용 관리자*).
1. **보고서** > **장바구니의 제품**(으)로 이동합니다.

<u>예상 결과</u>:

**모든 스토어 보기** 스토어 보기 범위 내에서 필터링할 때 제품 필터링은 해당 특정 범위에 설정된 값을 가져와야 합니다.

<u>실제 결과</u>:

저장소 보기 범위에서 재정의된 값은 &quot;모든 저장소 보기&quot; 저장소 보기 범위에서 필터링할 때도 고려됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
