---
title: 'ACSD-51358: 예약 업데이트가 누락됨'
description: ACSD-51358 패치를 적용하여 종료 날짜 없이 예약된 업데이트에 변경 사항이 적용되면 동일한 엔터티에서 다른 예약된 업데이트가 제거되는 Adobe Commerce 문제를 해결합니다.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358: 예약 업데이트가 누락되었습니다.

ACSD-51358 패치는 종료 날짜 없이 예약된 업데이트 의 변경 사항이 동일한 엔터티에서 다른 예약된 업데이트를 제거하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51358입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

종료 날짜 없이 예약된 업데이트가 변경되면 동일한 엔터티에서 다른 예약된 업데이트가 제거됩니다.

<u>재현 단계</u>:

1. 종료 날짜 없이 **[!UICONTROL scheduled update]**&#x200B;을(를) 만듭니다(*업데이트 1*).
1. 첫 번째 업데이트와 시작 날짜가 같은 새 **[!UICONTROL scheduled update]**&#x200B;을(를) 만들되, 다음 날과 종료 날짜(*업데이트 2*)를 추가하십시오.
1. 1단계(*업데이트 1*)에서 만든 **[!UICONTROL scheduled update]** 편집 및 변경 내용 저장

<u>예상 결과</u>

(*업데이트 1*)을(를) 편집할 때 (*업데이트 2*)은(는) **[!UICONTROL schedule update]** 목록에 남아 있어야 합니다.

<u>실제 결과</u>

(*업데이트 1*)을(를) 편집할 때 (*업데이트 2*)이(가) **[!UICONTROL schedule update]** 목록에서 제거되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>)을 참조하세요.
