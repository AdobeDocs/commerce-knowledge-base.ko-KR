---
title: 'ACSD-48234: [!UICONTROL Display Out of Stock Products]을(를) 사용하도록 설정한 경우 카탈로그 검색 결과가 잘못된 범주 항목 수입니다.'
description: '[!UICONTROL Display Out of Stock Products] 옵션이 활성화된 경우 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시되는 Adobe Commerce 문제를 해결하려면 ACSD-48234 패치를 적용하십시오.'
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: 카탈로그 검색 결과에 잘못된 범주 항목 수 **[!UICONTROL Display Out of Stock Products]**&#x200B;이(가) 사용되었습니다.

ACSD-48234 패치는 **[!UICONTROL Display Out of Stock Products]** 옵션이 활성화된 경우 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-48234입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.


## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Display Out of Stock Products]** 옵션을 사용하도록 설정한 경우 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**(으)로 이동하여 **[!UICONTROL color]** 특성을 엽니다.
1. 주황색과 녹색과 같은 두 가지 옵션을 추가합니다. 속성을 저장합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**(으)로 이동한 다음 **[!UICONTROL color]** 특성을 **[!UICONTROL Default]** 특성 집합에 추가합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]**(으)로 이동한 다음 **[!UICONTROL Display Out of Stock Products]**&#x200B;을(를) _예_(으)로 설정합니다.
1. 범주 &quot;cat1&quot;을 만듭니다.
1. 다음 두 가지 제품을 만듭니다.
   1. 이름: prod1, 색상: 주황색, 범주: cat1.
   1. 이름: prod2, 색상: 녹색, 범주: cat1.
1. 상점 앞에서 cat1 카테고리를 엽니다.
1. 레이어 탐색에서 주황색 색상을 선택합니다.

<u>예상 결과</u>:

prod1 제품만 표시됩니다.

<u>실제 결과</u>:

prod1 및 prod2 제품이 모두 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
