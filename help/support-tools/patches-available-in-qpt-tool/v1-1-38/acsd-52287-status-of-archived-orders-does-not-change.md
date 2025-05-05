---
title: 'ACSD-52287: 보관된 주문의 상태가 변경되지 않음'
description: ACSD-52287 패치를 적용하여 대변 메모가 제출된 후 그리드에서 보관된 주문의 상태가 *완료됨*에서 *마감됨*으로 변경되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287: 보관된 주문의 상태가 변경되지 않음

ACSD-52287 패치는 대변 메모가 제출된 후 보관된 주문의 상태가 그리드에서 *완료됨*&#x200B;에서 *마감됨*(으)로 변경되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52287입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

보관된 주문의 상태는 대변 메모가 제출된 후 그리드에서 *완료됨*&#x200B;에서 *마감됨*(으)로 변경되지 않습니다.

<u>재현 단계</u>:

1. *[!UICONTROL Asynchronous Indexing]* 구성.
   * 관리 사이드바에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**(으)로 이동합니다.
   * 왼쪽 패널에서 **[!UICONTROL Advanced]** 섹션을 확장하고 아래의 **[!UICONTROL Developer]**&#x200B;을(를) 선택합니다.
   * **[!UICONTROL Grid Settings]** 섹션을 확장합니다.
   * *[!UICONTROL Asynchronous indexing]*&#x200B;을(를) *예*(으)로 설정합니다.
   * **[!UICONTROL Save Config]**&#x200B;을(를) 클릭합니다.
1. *[!UICONTROL Order Archive]* 구성
   * 관리 사이드바에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**(으)로 이동합니다.
   * 왼쪽 패널에서 **[!UICONTROL Sales]** 섹션을 확장하고 아래의 **[!UICONTROL Sales]**&#x200B;을(를) 선택합니다.
   * **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** 섹션을 확장합니다.
   * *[!UICONTROL Enable Archiving]*&#x200B;을(를) *예*(으)로 설정합니다(나머지 구성은 기본값으로 둡니다).
   * **[!UICONTROL Save Config]**&#x200B;을(를) 클릭합니다.
1. 프론트 엔드에 주문을 넣으세요.
1. [!DNL cron]을(를) 실행하여 *[!UICONTROL Admin Order Grid]*&#x200B;에 표시하십시오.
1. 주문 상태를 *완료*(으)로 업데이트하려면 주문을 인보이스하고 배송하십시오.
1. [!DNL cron]을(를) 실행하여 *[!UICONTROL Sales Order Grid]*&#x200B;을(를) 최신 주문 상태로 업데이트합니다.
1. 주문을 보관합니다.
1. *[!UICONTROL Archived order grid]*(으)로 이동합니다.
1. 보관된 주문을 열고 [!UICONTROL Credit Memo]을(를) 만들어 [!UICONTROL Order status]을(를) 오프라인으로 전환합니다. *마감됨*.
1. [!DNL cron]을(를) 몇 번 실행합니다.
1. *[!UICONTROL Archived order grid]*&#x200B;에서 새 주문 상태를 확인하십시오.

<u>예상 결과</u>:

주문이 *마감됨*(으)로 표시됩니다.

<u>실제 결과</u>:

순서가 *완료*(으)로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
