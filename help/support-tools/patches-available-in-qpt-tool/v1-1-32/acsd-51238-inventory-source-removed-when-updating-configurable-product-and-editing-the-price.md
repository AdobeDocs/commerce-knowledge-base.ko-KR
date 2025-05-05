---
title: 'ACSD-51238: 구성 가능한 제품을 업데이트하고 가격을 편집할 때 재고 소스가 제거됨'
description: ACSD-51238 패치를 적용하여 구성 가능한 제품을 업데이트하고 가격을 편집할 때 인벤토리 소스가 제거되는 Adobe Commerce 문제를 해결합니다.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: 구성 가능한 제품을 업데이트하고 가격을 편집할 때 재고 출처가 제거됩니다.

ACSD-51238 패치는 구성 가능한 제품을 업데이트하고 가격을 편집할 때 인벤토리 소스가 제거되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51238입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품을 업데이트하고 가격을 편집할 때 재고 출처가 제거됩니다.

<u>재현 단계</u>:

1. **[!DNL Inventory module]**(으)로 **[!DNL Adobe Commerce]** 설치
1. **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]**(으)로 이동하여 *원본 두 개* 및 *재고 두 개*&#x200B;를 만듭니다.
1. **[!UICONTROL configurable product]**&#x200B;을(를) 만들어 **[!UICONTROL default sources]** 또는 **[!UICONTROL newly created sources]**&#x200B;에 할당합니다.
1. **[!UICONTROL next button]**&#x200B;을(를) 클릭하고 제품을 *저장*&#x200B;합니다.
1. 이제 동일한 **[!UICONTROL Configurable Product]**&#x200B;을(를) 편집하고 **[!UICONTROL Configuration tab]** 내부의 **[!UICONTROL Edit Configuration]**&#x200B;을(를) 클릭합니다.
1. `Step 3: Bulk Images,Price and Quantity`에서 `price`을(를) 변경하고 `Quantity` 및 `Images`을(를) 각각 `Skip quantity at this time` 및 `Skip image uploading at this time`(으)로 둡니다.
1. **[!UICONTROL next button]**&#x200B;을(를) 클릭하고 제품을 생성합니다.

<u>예상 결과</u>

**[!UICONTROL Configuration tab]** 내의 소스당 수량은 비워둘 수 없습니다.

<u>실제 결과</u>

**[!UICONTROL Configuration tab]** 내의 소스당 수량이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>)을 참조하세요.
