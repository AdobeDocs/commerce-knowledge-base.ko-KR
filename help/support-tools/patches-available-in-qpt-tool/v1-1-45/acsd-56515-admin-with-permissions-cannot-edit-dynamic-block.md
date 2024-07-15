---
title: 'ACSD-56515: 웹 사이트 수준 권한이 있는 관리자가 [!UICONTROL Dynamic Block]을(를) 편집할 수 없음'
description: 웹 사이트 수준 권한이 있는 관리자가 [!UICONTROL Dynamic Block]을(를) 추가하거나 편집할 수 없는 Adobe Commerce 문제를 해결하려면 ACSD-56515 패치를 적용하십시오.
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515: 웹 사이트 수준 권한이 있는 관리자가 [!UICONTROL Dynamic Block]을(를) 편집할 수 없습니다.

ACSD-56515 패치는 웹 사이트 수준 권한이 있는 관리자가 [!UICONTROL Dynamic Block]을(를) 추가하거나 편집할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56515입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

웹 사이트 수준 권한이 있는 관리자가 [!UICONTROL Dynamic Block]을(를) 추가하거나 편집할 수 없습니다.

<u>재현 단계</u>:

1. 스토어와 스토어를 사용하여 보조 웹 사이트를 만듭니다.
1. **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**(으)로 이동하여 사용 가능한 모든 리소스로 보조 웹 사이트 범위로 제한된 사용자 역할을 만듭니다.
1. 위에서 만든 역할을 사용하여 관리자 사용자를 만듭니다.
1. 제한된 관리자로 로그인하고 [!UICONTROL Dynamic Block]을(를) 만듭니다.

<u>예상 결과</u>:

웹 사이트에 대한 제한이 있는 관리자는 [!UICONTROL Dynamic Block]을(를) 만들 수 있습니다.

<u>실제 결과</u>:

다음 오류가 발생했습니다. *이 항목을 보려면 더 많은 권한이 필요합니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
