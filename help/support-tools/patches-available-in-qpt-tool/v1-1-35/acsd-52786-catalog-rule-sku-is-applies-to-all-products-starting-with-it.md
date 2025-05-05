---
title: 'ACSD-52786: 카탈로그 규칙 *[!UICONTROL SKU is]*은(는) SKU로 시작하는 모든 제품에 적용됩니다.'
description: ACSD-52786 패치를 적용하여 카탈로그 규칙 조건 *[!UICONTROL SKU is]*이(가) 지정된 SKU로 시작하는 모든 제품에 적용되는 Adobe Commerce 문제를 해결합니다.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: 카탈로그 규칙 &quot;*[!UICONTROL SKU is]*&quot;이(가) SKU로 시작하는 모든 제품에 적용됩니다.

ACSD-52786 패치는 지정된 SKU로 시작하는 모든 제품에 카탈로그 규칙 조건 *[!UICONTROL SKU is]*&#x200B;이(가) 적용되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52786입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카탈로그 규칙 조건 *[!UICONTROL SKU is]*&#x200B;은(는) 지정된 SKU로 시작하는 모든 제품에 적용됩니다.

<u>재현 단계</u>:

1. SKU &quot;24&quot;와 SKU &quot;24-MB01&quot;의 두 제품을 만듭니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**(으)로 이동합니다.
1. 다음 조건을 적용합니다.
   * 이 조건 중 *[!UICONTROL If **&#x200B;모두&#x200B;**&#x200B;은(는)**&#x200B; TRUE &#x200B;**]*: *[!UICONTROL SKU is 24]*&#x200B;입니다.
1. 액션에서 할인 금액을 설정합니다.
1. **[!UICONTROL Save and Apply]**&#x200B;을(를) 클릭합니다.
1. 캐시를 플러시합니다.
1. 가게 앞에 가셔서 24MB01의 가격을 확인해 보세요

<u>예상 결과</u>:

카탈로그 규칙은 SKU가 24와 같은 단일 제품에만 적용됩니다.

<u>실제 결과</u>:

카탈로그 규칙 조건 *[!UICONTROL SKU is]*&#x200B;은(는) 지정된 SKU로 시작하는 모든 제품에 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
