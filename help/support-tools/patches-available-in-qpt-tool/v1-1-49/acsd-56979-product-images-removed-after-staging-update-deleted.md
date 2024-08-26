---
title: 'ACSD-56979: 스테이징 업데이트 삭제 후 제품 이미지가 제거됨'
description: ACSD-56979 패치를 적용하여 스테이징 업데이트를 삭제한 후 제품 이미지가 제거되는 Adobe Commerce 문제를 해결합니다
feature: Products
role: Admin, Developer
source-git-commit: 8e916feab8be9d92d047fae8861a479070d448e8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-56979: 스테이징 업데이트 삭제 후 제거된 제품 이미지

ACSD-56979 패치는 스테이징 업데이트를 삭제한 후 제품 이미지가 제거되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56979입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 및 Magento Open Source 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 이미지는 스테이징 업데이트를 삭제한 후 제거됩니다.

<u>재현 단계</u>:

1. Commerce 관리 사이드바에서 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 제품을 만듭니다.
1. **[!UICONTROL Images and Videos]**&#x200B;에서 이미지를 업로드하고 제품을 저장합니다.
1. **[!UICONTROL Scheduled Changes]** 상자에서 **[!UICONTROL Schedule New Update]**&#x200B;을(를) 선택합니다.
   1. 미래의 시작 날짜를 몇 분 선택하십시오.
   1. 종료 날짜는 선택하지 마십시오.
1. **[!UICONTROL Scheduled Changes]** 상자에서 **[!UICONTROL View/Edit]** 링크를 선택합니다.
1. **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]**(으)로 이동한 다음 **[!UICONTROL Done]**&#x200B;을(를) 선택합니다.
1. 페이지를 새로 고칩니다.

<u>예상 결과</u>:

예정된 시작 날짜 이전에 업데이트가 제거되므로 제품은 그대로 유지되어야 합니다.

<u>실제 결과</u>:

이미지 콘텐츠가 손실되어 0바이트를 표시합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
