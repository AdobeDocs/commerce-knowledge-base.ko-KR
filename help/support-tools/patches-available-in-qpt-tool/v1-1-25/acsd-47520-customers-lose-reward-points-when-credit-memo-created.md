---
title: 'ACSD-47520: 대변 메모가 생성되면 고객이 보상 포인트를 잃음'
description: ACSD-47520 패치를 적용하여 대변 메모가 생성될 때 고객이 보상 포인트를 잃는 Adobe Commerce 문제를 해결합니다.
exl-id: 748b4e05-981d-49f6-a4f5-b121d57085f4
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47520: 대변 메모가 생성되면 고객이 보상 포인트를 잃음

ACSD-47520 패치는 대변 메모가 생성될 때 고객이 보상 포인트를 잃는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47520입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객은 대변 메모가 생성되면 보상 포인트를 잃게 됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자 > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**(으)로 이동합니다.
1. 설정을 변경합니다.
   * **[!UICONTROL Enable Reward Points Functionality]** = _예_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _예_
   * **[!UICONTROL Customers May See Reward Points History]** = _예_
   * **[!UICONTROL Refund Reward Points Automatically]** = _아니요_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _예_
1. 관리자 > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]**(으)로 이동한 다음 **[!UICONTROL Add New Rate]**&#x200B;을(를) 클릭합니다.
1. 새 비율(1:1)을 추가하고 캐시를 플러시합니다.
1. 고객을 만들고 이 계정에 10개의 보상 포인트를 추가합니다.
1. 관리자 > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > 이전 단계에서 만든 고객을 선택합니다.
1. 가격이 보상 포인트보다 큰 제품을 선택합니다.
1. 모든 결제 방법 및 보상 포인트를 통해 주문합니다.
1. 주문에 대한 송장을 생성합니다.
1. 대변 메모를 생성하되 보상 포인트는 환불하지 마십시오.

<u>예상 결과</u>:

* 관리자는 보상 포인트를 환불할 수 있습니다.

* 주문 상태가 마감됩니다.

<u>실제 결과</u>:

* 보상 포인트를 환불해 줄 방법이 없습니다.

* 주문 상태는 **[!UICONTROL Completed]**&#x200B;입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
