---
title: 'MDVA-34012 패치: 오류 시 속성 확인란이 변경됨'
description: MDVA-34012 패치는 오류로 인해 일정 업데이트 후 특성에 대한 확인란이 변경되는 문제를 해결합니다.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-34012 패치: 오류 시 속성 확인란이 변경됨

MDVA-34012 패치는 오류로 인해 일정 업데이트 후 특성에 대한 확인란이 변경되는 문제를 해결합니다.

이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17이 설치되었습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.1 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. Admin에 로그인한 다음 로 이동합니다. **카탈로그 > 제품**.
1. 간단한 제품을 편집합니다.
1. 스토어 뷰를 특정 스토어 뷰로 변경합니다.
1. 을(를) 사용하여 제품 저장 **기본값 사용** 속성에 대해 선택된 확인란(예: **제품 활성화** attribute).
1. 클릭 **새 업데이트 예약** 일부 변경 사항을 예약하려면 다음을 수행하십시오. **가격** 또는 **특별 가격** 특정 스토어 조회수).
1. 변경 사항이 완료될 때까지 기다립니다.
1. 제품을 확인합니다. 확인란을 선택 취소해야 하며 특정 저장소 속성 값이 있어야 합니다.

<u>예상 결과</u>:

속성에 대한 확인란은 동일하게 유지되어야 하며 스케줄 업데이트 후에는 예상대로 변경되지 않습니다.

<u>실제 결과</u>:

속성에 대한 확인란은 예약 업데이트 후에 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT 도구에서 사용할 수 있는 다른 패치에 대한 자세한 내용은 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
