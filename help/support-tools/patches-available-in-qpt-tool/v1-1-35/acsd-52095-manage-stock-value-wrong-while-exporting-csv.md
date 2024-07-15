---
title: 'ACSD-52095: CSV를 내보내는 동안 재고 값 관리가 잘못됨'
description: ACSD-52095 패치를 적용하여 CSV를 내보내는 동안 제품 관리 스톡 값이 잘못된 Adobe Commerce 문제를 해결합니다.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: CSV를 내보내는 동안 [!UICONTROL Manage Stock] 값이 잘못되었습니다.

ACSD-52095 패치는 CSV를 내보내는 동안 제품 `manage_stock` 값이 잘못된 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52095입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 내보내기 후 CSV 파일에서 `manage_stock` 값이 0으로 잘못 설정되었습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**(으)로 이동하여 **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*&#x200B;을(를) 설정합니다.
1. 새 제품을 만들고 저장합니다.
1. **[!UICONTROL System]** > **[!UICONTROL Export]**(으)로 이동합니다.
1. *[!UICONTROL Entity Type]* = *[!UICONTROL Products]*&#x200B;을(를) 선택하고 제품을 내보냅니다.
1. 생성된 CSV 파일을 확인하십시오. `manage_stock` = 0, `use_config_manage_stock` = 1.
1. 다시 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**(으)로 이동한 다음 **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*&#x200B;을(를) 설정합니다.
1. **시스템** > **내보내기**(으)로 이동합니다.
*[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*&#x200B;을(를) 선택합니다.
1. 생성된 CSV 파일을 확인하십시오. `manage_stock` = 0, `use_config_manage_stock` = 1.
1. 관리자에서 제품을 열고 **[!UICONTROL Advanced Inventory]**(으)로 이동하여 **[!UICONTROL Manage Stock]** 값을 확인합니다.

<u>예상 결과</u>

제품에 대해 **[!UICONTROL Manage Stock]** 값을 사용하도록 설정하면 *1* 값이 됩니다.

<u>실제 결과</u>

제품에 대해 **[!UICONTROL Manage Stock]** 값을 사용하도록 설정하면 *0* 값이 됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)을 참조하세요.
