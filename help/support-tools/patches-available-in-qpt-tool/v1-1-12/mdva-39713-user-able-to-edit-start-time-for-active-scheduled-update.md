---
title: 'MDVA-39713: 사용자가 활성 예약 업데이트 시작 시간을 편집할 수 있음'
description: MDVA-39713 패치는 사용자가 활성 예약 업데이트의 시작 시간을 편집할 수 있는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39713입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: 사용자가 활성 예약 업데이트 시작 시간을 편집할 수 있음

MDVA-39713 패치는 사용자가 활성 예약 업데이트의 시작 시간을 편집할 수 있는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39713입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.3.6

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

활성 예약 업데이트의 시작 시간을 편집할 수 있습니다.

<u>재현 단계</u>:

1. 새 CMS 페이지를 만듭니다.
1. **새 업데이트 예약**&#x200B;을 선택하고 **시작 날짜**&#x200B;을(를) 현재 +1분으로 설정하십시오.
1. 로컬 환경에서 `bin/magento cron:run --group=staging` 명령을 실행하여 예약된 업데이트를 활성화합니다. 몇 분 정도 기다린 후 일정이 활성 상태인지 확인합니다.
1. 일정이 활성화되면 페이지를 새로 고칩니다.
1. 예약된 변경 내용 섹션에서 **보기/편집**&#x200B;을 클릭합니다.
1. +2분을 추가하여 시간을 편집하고 변경 사항을 저장합니다.
1. CMS 페이지를 저장합니다.
1. `bin/magento cron:run --group=staging` 명령을 다시 실행하십시오.
1. 예약된 업데이트의 **보기/편집**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

활성 예약된 업데이트의 시작 시간을 편집할 수 없습니다.

<u>실제 결과</u>:

동일한 ID &quot;11&quot;을(를) 가진 *항목(Magento\Cms\Model\Page)이 이미 있는 것과 같은 오류가 사용자에게 발생합니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
