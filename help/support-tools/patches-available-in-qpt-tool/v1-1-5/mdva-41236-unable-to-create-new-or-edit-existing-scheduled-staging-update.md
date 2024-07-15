---
title: 'MDVA-41236: 제품에 대해 새로 만들거나 기존 예약된 업데이트를 편집할 수 없음'
description: MDVA-41236 패치는 이전에 "종료 날짜"를 제거한 경우 사용자가 제품에 대해 새 업데이트를 만들거나 기존 예약된 업데이트를 편집할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41236입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236: 제품에 대해 새로 만들거나 기존 예약된 업데이트를 편집할 수 없음

MDVA-41236 패치는 이전에 &quot;종료 날짜&quot;를 제거한 경우 사용자가 제품에 대해 새 업데이트를 만들거나 기존 예약된 업데이트를 편집할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41236입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이전에 &quot;종료 날짜&quot;가 제거된 경우 사용자는 새 일정을 만들거나 기존 제품 일정을 편집할 수 없습니다.

<u>재현 단계</u>:

1. 상태가 *disable*(으)로 설정된 제품을 만듭니다.
1. 이 제품을 사용하려면 예약된 업데이트를 추가하십시오.
   * 향후 시작 및 종료 날짜를 추가합니다.
1. **종료 날짜**&#x200B;를 제거하여 예약된 업데이트를 편집합니다.
1. 일정을 다시 편집하고 **종료 날짜**&#x200B;를 추가해 보세요. 오류가 발생합니다.
1. 페이지를 새로 고치고 **예약된 업데이트 편집**(으)로 다시 이동합니다.
1. **업데이트에서 제거** > **업데이트 삭제**&#x200B;를 클릭합니다.
1. 이제 제품 편집 페이지 맨 위에 예약된 업데이트가 표시되지 않습니다.
1. 이전 기간과 겹치는 예약된 업데이트를 새로 만들어 보십시오.

<u>예상 결과</u>:

* 4단계에는 오류가 없습니다. 관리자는 일정이 아직 활성화되지 않았기 때문에 오류 없이 예약된 업데이트를 업데이트할 수 있습니다.
* 관리자 사용자는 이전 업데이트를 삭제하고 새 업데이트를 만들 수 있습니다.

<u>실제 결과</u>:

사용자에게 다음과 같은 오류 메시지가 표시됩니다.

*오류: 이 시간 범위에 향후 업데이트가 이미 있습니다. 다른 범위를 설정하고 다시 시도하십시오.*


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
