---
title: 'MDVA-34102: 판매 가능한 수량 불일치'
description: MDVA-34102 패치는 관리자의 제품 그리드 및 제품 편집 페이지에서 비활성화된 제품에 대해 기본 재고 수량이 0인 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-34102입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: 판매 가능한 수량 불일치

MDVA-34102 패치는 관리자의 제품 그리드 및 제품 편집 페이지에서 비활성화된 제품에 대해 기본 재고 수량이 0인 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-34102입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 스토어 및 스토어 조회수가 있는 웹 사이트 두 개를 설정합니다.
1. 추가 소스 및 재고를 생성합니다.
1. 간단한 제품 추가:
   * **제품 사용** = *아니요*&#x200B;를 설정합니다.
   * 수량이 0보다 큰 **Source 항목 상태** = *재고 있음*(예: **기본 재고** = *123* 및 **영국 재고** = *123*)의 두 소스를 할당합니다.
1. 제품을 저장합니다.
1. **제품 판매 수량** 탭을 확인하십시오.

<u>예상 결과</u>:

기본 주식과 영국 주식 모두 = *123.*

관리자의 제품 그리드 및 제품 편집 페이지에 비활성화된 제품에 대한 기본 재고 수량이 올바르게 표시됩니다.

<u>실제 결과</u>:

기본 재고 = *0* 및 영국 재고 = *123.*

기본 재고 수량은 관리자의 제품 그리드 및 제품 편집 페이지에서 비활성화된 제품에 대해 0입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
