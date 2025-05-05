---
title: 'ACSD-53309: 사용자 지정 가능한 옵션 및 [!UICONTROL Regular Price] 레이블에 대한 세금 응용 프로그램이 불완전합니다.'
description: 사용자 지정 가능한 옵션이 선택되어 있을 때 '[!UICONTROL Regular Price]' 레이블에 세금이 완전히 적용되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-53309 패치를 적용합니다.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: de9b151e-6f92-4231-9e9f-4818c2961782
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-53309: 사용자 지정 옵션 및 &#39;[!UICONTROL Regular Price]&#39; 레이블에 대한 세금 응용 프로그램이 불완전합니다.

ACSD-53309 패치는 사용자 지정 가능한 옵션을 선택할 때 &#39;[!UICONTROL Regular Price]&#39; 레이블에서 세금이 완전히 적용되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53309입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 가능한 옵션을 선택할 때 &#39;[!UICONTROL Regular Price]&#39; 레이블에 세금이 완전히 반영되지 않습니다.

<u>재현 단계</u>:

1. 관리자 패널에 로그인합니다.
1. 세금 설정을 구성하려면 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**(으)로 이동합니다.

   * [!UICONTROL Tax Classes]:

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *영국*&#x200B;을 설정합니다.

1. 다음 *[!UICONTROL Tax Rate]* 및 *[!UICONTROL Tax Rules]*&#x200B;을(를) 만듭니다.

   * [!UICONTROL Country] = 미국
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. 간단한 제품을 만들고 다음을 설정합니다.
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * 드롭다운에서 type 을 custom option으로 설정하고 price 를 15% 로 설정합니다.
1. 상점 첫 화면에서 만든 간단한 품목의 제품 페이지로 이동합니다.
1. 만들어진 사용자 지정 옵션 *15%*&#x200B;을(를) 선택하십시오.

<u>예상 결과</u>:

* 선택한 사용자 정의 옵션에 20% 세금이 적용됩니다.
* &#39;[!UICONTROL Regular Price]&#39; = 151.80.

<u>실제 결과</u>:

* 선택한 사용자 정의 옵션에는 20% 세금이 적용되지 않습니다.
* &#39;[!UICONTROL Regular Price]&#39; = 148.50.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
