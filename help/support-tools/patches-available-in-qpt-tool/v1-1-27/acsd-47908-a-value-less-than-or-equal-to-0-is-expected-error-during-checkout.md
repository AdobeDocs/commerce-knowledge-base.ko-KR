---
title: 'ACSD-47908: *0보다 작거나 같은 값이 필요합니다.* 체크아웃 중 오류가 발생했습니다.'
description: ACSD-47908 패치를 적용하여 Adobe Commerce 오류를 수정합니다 *체크아웃 중 배송 단계에서 소스 및 수량을 선택할 경우 0보다 작거나 같은 값이 예상됩니다*.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *체크아웃 중에 0보다 작거나 같은 값이 필요합니다* 오류

ACSD-47908 패치는 체크아웃 중 배송 단계에서 소스 및 수량을 선택할 때 *0보다 작거나 같은 값이 예상됨* 오류를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47908입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

체크아웃 중에 배송 단계에서 소스 및 수량을 선택할 때 다음 오류가 발생합니다. *0보다 작거나 같은 값이 필요합니다*.

<u>필수 구성 요소</u>:

Adobe Commerce Inventory management(MSI) 모듈을 설치합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]**(으)로 이동하여 여러 소스를 구성합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]**(으)로 이동하여 새 주식을 만드십시오.
   * 이제 소스를 새 재고에 할당합니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 제품을 하나 이상 편집하십시오.
   * 제품이 새 출처에 할당되었는지 확인하고 사용 가능한 수량을 지정합니다.
1. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동하여 새 주문을 만듭니다.
1. 그 제품들을 주문에 추가하여 주문합니다.
1. **[!UICONTROL Ship]**&#x200B;을(를) 클릭합니다.
1. 출고할 출처를 선택합니다.
1. 출하할 각 품목의 수량을 지정합니다.
1. 페이지를 다시 로드합니다.
1. **[!UICONTROL Proceed to Shipment]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

새 배송 페이지가 오류 없이 열립니다.

<u>실제 결과</u>:

* 입력한 수량을 확인할 수 없습니다.
* 다음 오류가 발생했습니다. *0*&#x200B;보다 작거나 같은 값을 입력하십시오.

  그러나 오류가 일관되지 않으며 항상 나타나는 것은 아닙니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
