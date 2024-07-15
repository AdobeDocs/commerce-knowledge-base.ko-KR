---
title: 'Adobe Commerce 관리자에서 알림을 해제할 때 ACSD-47336: [!UICONTROL Something went wrong] 오류 발생'
description: ACSD-47336 패치를 적용하여  [!DNL Commerce] Admin에서 알림을 해제할 때 사용자에게 [!UICONTROL Something went wrong] 오류가 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: Adobe Commerce 관리자의 알림을 해제할 때 _[!UICONTROL Something went wrong]_오류가 발생했습니다.

ACSD-47336 패치는 [!DNL Commerce] 관리자의 알림을 해제할 때 사용자에게 _[!UICONTROL Something went wrong]_오류가 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47336입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법): 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Commerce] 관리자의 알림을 해제할 때 _[!UICONTROL Something went wrong]_오류가 표시됩니다.

<u>재현 단계</u>:

1. 대량 작업을 수행합니다(예: 제품 그리드에서 제품 속성의 대량 업데이트).
1. 작업을 완료합니다(예: `bin/magento queue:consumer:start product_action_attribute.update` 실행).
1. [!DNL Commerce] 관리 페이지를 새로 고치고 관리자 알림 섹션을 확장한 다음 **[!UICONTROL Dismiss All Completed Tasks]** 링크를 클릭합니다.

<u>예상 결과</u>:

완료된 작업을 지울 때 _[!UICONTROL Something went wrong]_오류가 표시되지 않아야 합니다.

<u>실제 결과</u>:

_[!UICONTROL Something went wrong]_오류가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
