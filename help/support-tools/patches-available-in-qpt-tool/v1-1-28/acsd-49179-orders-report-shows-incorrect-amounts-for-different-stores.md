---
title: 'ACSD-49179: 주문 보고서에 서로 다른 스토어에 대한 잘못된 금액이 표시됩니다.'
description: ACSD-49179 패치를 적용하여 매장마다 통화가 다른 경우 주문 보고서에 잘못된 금액이 표시되는 Adobe Commerce 문제를 수정하십시오.
exl-id: 01e4cd2d-6c33-4cf5-bf31-bbc34eaaed1a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-49179: 주문 보고서에 서로 다른 스토어에 대한 잘못된 금액이 표시됩니다.

ACSD-49179 패치를 사용하면 서로 다른 스토어에 대해 서로 다른 통화를 사용하는 경우 주문 보고서에 잘못된 금액이 표시되는 문제를 해결할 수 있습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49179입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 보고서는 서로 다른 스토어에 대해 서로 다른 통화의 경우 잘못된 금액을 표시합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]**(으)로 이동하여 [!UICONTROL Catalog Price Scope] = [!UICONTROL Website]을(를) 설정합니다.
1. 추가 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]**(으)로 이동하여 다음을 설정합니다.
   * 기본 구성:
      * 기본 통화: USD
      * 기본 표시 통화: USD
      * 허용된 통화: EUR, USD 및 THB (태국 바트)
   * 기본 웹 사이트:
      * 기본 통화: EUR
      * 기본 표시 통화: EUR
      * 허용된 통화: EUR
   * 추가 새 웹 사이트:
      * 기본 통화: THB (태국 바트)
      * 기본 표시 통화: THB (태국 바트)
      * 허용된 통화: THB (태국 바트)
1. **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]**(으)로 이동하여 THB에 대한 빈 전환율을 설정합니다(요금을 1.0000으로 설정).
1. 제품을 만들어 두 웹 사이트에 할당한 다음 이전에 만든 추가 웹 사이트에서 이 제품을 주문합니다.
1. 주문의 상태가 *처리 중*&#x200B;인지 확인하세요(인보이스 발행).
1. 백엔드에서 **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동합니다.
1. 통계를 새로 고치려면 **[!UICONTROL Yellow]** 경고를 클릭하십시오.
1. 이전에 만든 추가 웹 사이트에서 보고서 범위를 설정하고 필터를 다음과 같이 설정합니다.
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: 테스트 순서가 지정된 같은 날
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>예상 결과</u>:

Sales total은 웹 사이트의 통화로 변환된 올바른 금액을 보여 줍니다.

<u>실제 결과</u>:

총계는 0입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
