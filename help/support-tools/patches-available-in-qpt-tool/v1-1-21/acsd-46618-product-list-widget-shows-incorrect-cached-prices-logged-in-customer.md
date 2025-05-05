---
title: "ACSD-46618: 제품 목록 위젯에 로그인한 고객에 대해 잘못된 캐시된 가격이 표시됨"
description: 로그인한 고객에 대해 제품 목록 위젯에 잘못된 캐시된 가격이 표시되는 Adobe Commerce 문제를 해결하려면 패치를 적용합니다.
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618: 제품 목록 위젯에 로그인한 고객에 대해 잘못된 캐시된 가격이 표시됨

ACSD-46618 패치는 로그인한 고객에 대해 제품 목록 위젯에 잘못된 캐시된 가격이 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html?lang=ko) 1.1.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-46618입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

ACSD-46618 패치는 로그인한 고객에 대해 제품 목록 위젯에 잘못된 캐시된 가격이 표시되는 문제를 해결합니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리에서 **[!UICONTROL Stores]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Configuration]**&#x200B;을(를) 선택하고 **[!UICONTROL Sales]**&#x200B;을(를) 확장한 다음 **[!UICONTROL Tax]**&#x200B;을(를) 선택합니다. 세금을 포함한 가격과 제외한 가격을 표시하도록 세금 설정을 업데이트합니다.
1. **[!UICONTROL Enable Cross Border Trade]** = _예_&#x200B;를 설정합니다.
1. 미국에만 적용되는 세금 규칙을 생성합니다.
1. 두 개 이상의 제품을 포함하는 위젯을 홈 페이지에 추가합니다.
1. 미국 주소와 미국 주소가 아닌 주소로 두 고객을 만듭니다.
1. 상점에서 미국 고객을 사용하여 로그인합니다. 페이지가 캐시되었는지 확인합니다.
1. 홈 페이지 위젯에 표시되는 가격을 확인합니다.
1. 미국 이외의 고객을 사용하여 로그아웃하고 로그인합니다.

<u>예상 결과</u>:

홈페이지 위젯에 표시되는 가격은 고객의 주소에 해당합니다.

<u>실제 결과</u>:

홈 페이지 위젯은 미국 외 지역 고객을 위한 세금을 사용한 가격을 보여줍니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 자세한 내용은 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
