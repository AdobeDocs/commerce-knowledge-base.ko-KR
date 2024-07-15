---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** 데이터가 스토어 보기에서 제대로 업데이트되지 않음'
description: ACSD-53658 패치를 적용하여 **[!UICONTROL Recently Viewed Product]** 데이터가 스토어 보기에서 제대로 업데이트되지 않는 Adobe Commerce 문제를 해결합니다.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** 데이터가 저장소 보기에서 제대로 업데이트되지 않았습니다.

ACSD-53658 패치는 저장소 보기에서 **[!UICONTROL Recently Viewed Product]** 데이터가 제대로 업데이트되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-53658입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

저장소 보기에서 **[!UICONTROL Recently Viewed Product]** 데이터가 제대로 업데이트되지 않았습니다.

<u>재현 단계</u>:

1. 관리자 패널에 로그인합니다.
1. 기본 웹 사이트에 대한 두 번째 스토어 보기를 만듭니다.
1. 간단한 제품을 만듭니다.
1. 새 스토어 보기에 대해 다른 제품 이름을 설정합니다.
1. **[!UICONTROL Recently Viewed Product]** 위젯을 만듭니다.
1. 홈 페이지에 표시하도록 이 위젯을 구성합니다.
1. 기본 스토어 보기에서 상점 첫 화면의 제품 페이지를 엽니다.
1. 홈 페이지를 엽니다.
1. 스토어 전환기를 사용하여 두 번째 스토어 보기로 전환합니다.

<u>예상 결과</u>:

위젯에서 제품 이름이 업데이트됩니다.

<u>실제 결과</u>:

위젯에서 제품 이름이 업데이트되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
