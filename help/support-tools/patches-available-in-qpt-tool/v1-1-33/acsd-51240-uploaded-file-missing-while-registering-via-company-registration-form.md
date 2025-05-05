---
title: 'ACSD-51240: 회사 등록 양식을 통해 등록하는 동안 업로드된 파일이 누락됨'
description: 회사 등록 양식을 통해 등록하는 동안 업로드한 파일이 누락된 Adobe Commerce 문제를 해결하려면 ACSD-51240 패치를 적용합니다.
exl-id: e5822c54-4e77-46b0-84b6-5e25c3845974
source-git-commit: e1fe8936c56f422ae591c6424d8a72621093db81
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240: 회사 등록 양식을 통해 등록하는 동안 업로드된 파일이 누락됨

>[!NOTE]
>
>이 패치는 [ACSD-55628](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md)(으)로 대체되었습니다.

ACSD-51240 패치는 회사 등록 양식을 통해 등록하는 동안 업로드된 파일이 누락되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51240입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>). 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 문제

회사 등록 양식을 통해 등록하는 동안 업로드된 파일이 누락되었습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *예*&#x200B;를 설정합니다.
1. **[!UICONTROL File]** 유형의 새 고객 특성을 만들고 **[!UICONTROL Show in StoreFront]** = *예*&#x200B;를 설정한 다음 **[!UICONTROL all forms]**&#x200B;을(를) 선택하십시오.
1. Storefront에서 새 회사를 만들고 새 속성에 대한 이미지를 업로드합니다.
Storefront에서 회사 및 관리자 사용자를 엽니다.

<u>예상 결과</u>:

업로드된 파일이 표시됩니다.

<u>실제 결과</u>:

업로드한 파일이 회사 페이지나 [!UICONTROL Commerce Admin]의 관리자 고객 페이지에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
