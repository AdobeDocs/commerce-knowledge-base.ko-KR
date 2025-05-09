---
title: 'ACSD-46865: [!UICONTROL asynchronous indexing]이(가) 활성화된 경우 [!UICONTROL shipment] 및 [!UICONTROL credit memo]이(가) 채워지지 않음'
description: ACSD-46865 패치를 적용하여 [!UICONTROL asynchronous indexing]이(가) 활성화된 경우 [!UICONTROL shipment] 및 [!UICONTROL credit memo] 그리드가 채워지지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL asynchronous indexing]을(를) 사용하도록 설정한 경우 [!UICONTROL shipment] 및 [!UICONTROL credit memo]이(가) 채워지지 않음

ACSD-46865 패치는 [!UICONTROL asynchronous indexing]을(를) 사용할 때 [!UICONTROL shipment] 및 [!UICONTROL credit memo] 그리드가 채워지지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-46865입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL asynchronous indexing]이(가) 활성화되면 [!UICONTROL Shipment] 및 [!UICONTROL credit memo] 그리드가 채워지지 않습니다.

<u>재현 단계</u>:

1. [!DNL Commerce] 관리자의 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *예*(으)로 이동합니다.
2. 다시 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*(으)로 이동합니다.
3. 구성 캐시를 정리합니다.
4. 간단한 제품에 대해 새로운 손님 주문을 합니다.
5. 크론 실행
6. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동하여 [!UICONTROL Commerce] 관리자의 주문을 열고 인보이스와 대변 메모를 생성합니다.
7. 주문을 [!UICONTROL Archive] (으)로 이동합니다.
8. 간단한 제품에 대해 다른 주문을 만듭니다.
9. 크론 실행
10. 신규 주문으로 이동하여 신규 선적, 송장 및 대변 메모를 생성합니다.
11. 크론 실행
12. 관리자에서 [!UICONTROL shipments], [!UICONTROL invoices] 및 [!UICONTROL credit memo] 그리드를 확인합니다.

<u>예상 결과</u>:

새 [!UICONTROL shipment], [!UICONTROL invoice] 및 [!UICONTROL credit memo]이(가) 표시됩니다.

<u>실제 결과</u>:

새 [!UICONTROL shipment], [!UICONTROL invoice] 및 [!UICONTROL credit memo]이(가) 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
