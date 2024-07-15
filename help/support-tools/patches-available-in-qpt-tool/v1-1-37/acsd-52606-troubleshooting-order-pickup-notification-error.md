---
title: 'ACSD-52606: 사용자가 "주문 알림 픽업 준비됨"을 클릭할 때 표시되는 오류 메시지'
description: ACSD-52606 패치를 적용하여 사용자가 **[!UICONTROL Notify Order is Ready for Pickup]을(를) 클릭할 때 오류 메시지가 표시되는 Adobe Commerce 문제를 **.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: 사용자가 &quot;주문 알림 픽업 준비됨&quot;을 클릭할 때 표시되는 오류 메시지

ACSD-52606 패치는 사용자가 **[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;을(를) 클릭할 때 *주문이 픽업될 준비가 되지 않았습니다* 오류 메시지가 표시되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52606입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 **[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;을(를) 클릭하면 *주문이 픽업될 준비가 되지 않았습니다* 오류 메시지가 화면에 표시됩니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 새 인스턴스를 설치합니다.
1. 새 소스 및 스톡을 만듭니다.
1. 기본 웹 사이트에 새 소스를 할당합니다.
1. 새로 생성된 소스에 대한 픽업 위치를 활성화합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**(으)로 이동하여 **[!UICONTROL In-Store Delivery]**&#x200B;을(를) 활성화합니다.
1. 모든 재고 및 *[!UICONTROL Manage Stock = No]*&#x200B;에 대해 *QTY=0*&#x200B;인 *재고* 단순 제품을 만들고 두 소스에 할당합니다.
1. 이전 단계에서 만든 제품으로 프론트엔드에서 주문을 만들고 *[!UICONTROL In-Store Pickup]*&#x200B;을(를) 게재 방법으로 선택합니다.
1. [관리]에서 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**(으)로 이동합니다.
1. **[!UICONTROL Notify order is ready for pickup]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

오류 없이 알림을 받습니다.

<u>실제 결과</u>:

다음 오류 메시지가 표시됩니다. *주문이 픽업할 준비가 되지 않았습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
