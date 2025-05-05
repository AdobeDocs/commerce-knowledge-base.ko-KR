---
title: 'ACSD-55628: 회사 등록 양식에 파일 업로드 중, 상점 첫 화면에서 고객 특성에 대한 파일 바꾸기'
description: ACSD-55628 패치를 적용하여 회사 등록 양식에 파일을 업로드하고 상점 첫 화면에서 고객 속성에 대한 파일을 대체할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: ca85b459-f72b-4663-85af-1f793935fe7e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-55628: 회사 등록 양식에 파일 업로드 중, 상점 첫 화면에서 고객 특성에 대한 파일 대체

>[!NOTE]
>
>이 패치는 [ACSD-51240](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md)을(를) 대체합니다.

ACSD-55628 패치는 회사 등록 양식에 파일을 업로드하고 상점 첫 화면에서 고객 속성에 대한 파일을 바꾸는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-55628입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2 &lt; 2.4.5 및 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

상점 첫 화면의 고객 특성에 대한 파일을 바꿀 수 없습니다.

<u>재현 단계</u>:

1. 다음 값으로 새 고객 속성을 만듭니다.

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *예*
   * *[!UICONTROL Forms to Use In]*: *사용 가능한 모든 옵션*

1. 상점 첫 화면에서 고객으로 로그인한 다음 **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**&#x200B;을(를) 엽니다.
1. 새 이미지를 업로드하고 저장합니다.
1. 페이지를 새로 고칩니다. 이전 이미지를 삭제하고 새 이미지를 업로드합니다. 변경 사항을 저장합니다.

<u>예상 결과</u>:

새 이미지가 저장됩니다.

<u>실제 결과</u>:

이전 이미지가 여전히 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
