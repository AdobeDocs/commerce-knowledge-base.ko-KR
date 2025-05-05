---
title: 'ACSD-54776: 선택 취소된 [!UICONTROL Use Default Value] 및 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 기본값이 아닌 제품 필드 값이 저장되지 않음'
description: ACSD-54776 패치를 적용하여 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 선택되지 않은 [!UICONTROL Use Default Value] 및 기본값이 아닌 제품 필드 값이 저장되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776: 선택되지 않은 *[!UICONTROL Use Default Value]* 및 기본값이 아닌 제품 필드 값이 저장되지 않았습니다.

>[!NOTE]
>
>이 패치는 QPT 1.1.35에서 릴리스된 [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) 패치를 대체합니다.

ACSD-54776 패치를 사용하면 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 선택되지 않은 **[!UICONTROL Use Default Value]** 및 기본값이 아닌 제품 필드 값이 저장되지 않는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54776입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

선택하지 않은 *[!UICONTROL Use Default Value]* 및 기본값이 아닌 제품 필드 값은 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 저장되지 않습니다.

<u>재현 단계</u>:

1. 백엔드로 이동하여 **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**(으)로 이동하고 새 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 간단한 제품을 만들고 저장한 다음 **[!UICONTROL Product in Websites]**&#x200B;에서 두 웹 사이트에 제품을 할당하십시오.
1. 2단계에서 새로 만든 스토어 보기로 범위를 변경합니다.
1. **[!UICONTROL Search Engine Optimization]**(으)로 이동하여 [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] 및 [!UICONTROL Meta Description]에 대한 **[!UICONTROL Use Default Value]** 확인란의 선택을 취소하십시오.
1. *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* 및 *[!UICONTROL Meta Description]* 필드에서 텍스트를 정리하고 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Search Engine Optimization]**(으)로 다시 이동

<u>예상 결과</u>

필드 및 확인란의 값이 저장됩니다.

<u>실제 결과</u>

필드 및 확인란의 값이 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>)을 참조하세요.
