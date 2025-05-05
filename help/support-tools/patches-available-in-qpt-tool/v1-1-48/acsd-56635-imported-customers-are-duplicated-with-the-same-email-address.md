---
title: 'ACSD-56635: 계정 공유를  [!DNL Global] (으)로 설정하면 가져온 고객이 중복됩니다.'
description: 계정 공유를  [!DNL Global] (으)로 설정한 상태에서 가져오기를 사용할 때 가져온 고객이 동일한 이메일 주소로 복제되는 Adobe Commerce 문제를 해결하려면 ACSD-56635 패치를 적용합니다.
feature: Customers, Attributes
role: Admin, Developer
exl-id: abd542a1-6764-4385-97a6-b46015363b42
source-git-commit: 880fc679afc853b514fddda56e570fe1a279a3d9
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: 계정 공유를 [!DNL Global] (으)로 설정하면 가져온 고객이 동일한 이메일 주소로 복제됩니다.

ACSD-56635 패치는 계정 공유가 [!DNL Global] (으)로 설정된 상태에서 가져오기를 사용할 때 가져온 고객이 동일한 이메일 주소로 복제되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56635입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

계정 공유를 [!DNL Global] (으)로 설정하면 가져온 고객이 동일한 이메일 주소로 복제됩니다.

<u>재현 단계</u>:

1. Adobe Commerce(2.4-develop b2b) **[!UICONTROL Admin]**&#x200B;에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**&#x200B;에 액세스합니다.
1. *[!UICONTROL Share Customer Accounts]* 설정을 *[!DNL Global]*(으)로 설정합니다.
1. 여러 웹 사이트 및 스토어 만들기:

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. *기본 웹 사이트* 아래에 전자 메일 주소를 <adb@yormail.com>(으)로 사용하여 관리자의 새 고객을 만드십시오.
1. **[!UICONTROL Admin]**&#x200B;에서 **[!UICONTROL System]** > **[!UICONTROL Import]**(으)로 이동합니다.
1. **[!UICONTROL Customer Entity Type]**&#x200B;을(를) *[!UICONTROL Customers Main File]*(으)로 선택합니다.
1. 다른 웹 사이트(예: ws1)에서 <adb@yormail.com>과(와) 동일한 전자 메일 주소를 사용합니다. 아래의 샘플 CSV 파일 customer.csv를 참조하십시오.
1. 가져오기를 완료하여 *ws1* 웹 사이트에서 만든 새 사용자를 동일한 전자 메일 주소로 봅니다.

customer.csv 콘텐츠:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>예상 결과</u>:

동일한 이메일 주소로 가져온 고객은 복제되지 않고 업데이트됩니다.

<u>실제 결과</u>:

고객 가져오기를 사용할 때 동일한 이메일 주소로 중복 고객이 만들어집니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
