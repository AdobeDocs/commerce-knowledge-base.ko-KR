---
title: 'ACSD-56246: 제품 업데이트를 예약하면 다중 선택 속성 값이 지워집니다'
description: ACSD-56246 패치를 적용하여 제품 업데이트를 예약하면 다중 선택 속성 값이 지워지는 Adobe Commerce 문제를 해결합니다.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: ddca8ac0-6aa8-4bf1-b8c2-4819758cb198
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56246: 제품 갱신을 예약하면 다중 선택 속성 값이 지워집니다.

ACSD-56246 패치는 제품 업데이트 일정을 잡으면 다중 선택 속성 값이 지워지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56246입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

예약된 제품 업데이트는 다중 선택 속성 값을 지웁니다.

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**(으)로 이동하여 다음 특성을 만듭니다.

   * 기본 레이블: 프로그램
   * 저장소 소유자에 대한 카탈로그 입력 유형: 다중 선택
   * 옵션 관리(속성 값): Choice, Sunscape, Safetyshield
   * 속성 코드: customer_program
   * 범위: 글로벌
   * 열에 추가 옵션: 아니요
   * 필터 옵션에서 사용: 아니요
   * Storefront 속성
   * 위치: *333*
   * Storefront에서 HTML 태그 허용: 아니요

1. 실행
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. 실행
   `bin/magento setup:upgrade`.
1. **[!UICONTROL Admin]** > 간단한 제품 선택 > 프로그램 속성에서 모든 항목 선택 > **[!UICONTROL Save the product]**(으)로 이동합니다.
1. 다음 분 내에 이 제품에 대한 업데이트를 예약하고 아래 명령을 실행하여 콘텐츠 스테이징이 작동하는지 확인하십시오.
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>예상 결과</u>:

제품의 **[!UICONTROL program]** 특성은 변경할 수 없습니다.

<u>실제 결과</u>:

제품의 **[!UICONTROL program]** 특성이 지워졌습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
