---
title: 'ACSD-48773: 잘못된 저장소에서 가져온 보상 포인트 이메일 템플릿'
description: ACSD-48773 패치를 적용하여 보상 지점 이메일 템플릿이 잘못된 저장소에서 가져간 Adobe Commerce 문제를 수정합니다.
exl-id: 96dda97c-5177-4883-ad2b-709928cb5f4d
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773: 잘못된 스토어에서 가져온 리워드 포인트 이메일 템플릿

ACSD-48773 패치는 보상 지점 이메일 템플릿을 잘못된 저장소에서 가져오는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48773입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

번들 제품이 웹 사이트에 할당되지 않은 경우 제품 가격 재지수가 작동하지 않습니다.

<u>재현 단계</u>:

1. 2개의 웹 사이트, 2개의 스토어 및 2개의 스토어 뷰를 만듭니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]**(으)로 이동하여 **[!UICONTROL Reviews]**&#x200B;을(를) 활성화합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**(으)로 이동합니다.
**[!DNL default website scope]**(으)로 전환하고 **[!UICONTROL Customer Support Sender Email]** 주소를 설정합니다(예: *support_base@example.com*).
**[!DNL second website scope]**(으)로 전환하고 **[!UICONTROL Customer Support Sender Email]** 주소를 다른 값으로 설정합니다(예: *support_second@example.com*).
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**(으)로 이동한 다음 **[!UICONTROL Share Customer Accounts]** = *웹 사이트당*&#x200B;을(를) 설정합니다.
1. **[!UICONTROL Reward Points]**&#x200B;에서 다음을 설정하십시오.
   **[!UICONTROL Enable Reward Points Functionality]** = *예*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *예*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** 및 설정 **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** 및 설정 **[!UICONTROL Email Sender]** = *고객 지원*
1. **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]**(으)로 이동하여 **[!UICONTROL Points/Currency]** 및 **[!UICONTROL Currency/Points]** 모두에 대한 두 번째 웹 사이트의 환율을 설정합니다.
1. 두 번째 웹 사이트에서 고객 계정을 만듭니다.
1. 두 번째 웹 사이트에서 고객으로 로그인합니다.
1. **[!UICONTROL Balance Updates]**&#x200B;에 대해 **[!UICONTROL Subscribe]**&#x200B;을(를) 사용하도록 설정해야 합니다.
1. 제품 리뷰를 제출합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**(으)로 이동합니다.
1. 새 검토의 상태를 ***[!UICONTROL Approved]*** 및 **[!UICONTROL Save]**(으)로 변경합니다.
1. 이메일이 도착할 때까지 기다립니다.

<u>예상 결과</u>:

보상 포인트 업데이트 이메일은 두 번째 웹 사이트 범위에 구성된 이메일 발신자가 전송해야 합니다.

<u>실제 결과</u>:

기본 웹 사이트 범위에 구성된 이메일 보낸 사람이 보상 포인트 업데이트 이메일을 보냈습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
