---
title: 'ACSD-47803: 사용 가능한 것으로 표시되는 재고 부족 구성 가능한 제품 견본'
description: ACSD-47803 패치를 적용하여 품절 구성 가능한 제품 견본이 사용 가능한 것으로 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 28b3f378-a790-4af6-9627-5bd8571523fd
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-47803: 구성 가능한 제품 견본이 사용 가능한 것으로 표시됨

ACSD-47803 패치는 재고 부족 구성 가능한 제품 견본이 사용 가능한 것으로 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47803입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

품절 구성 가능한 제품 견본이 사용 가능한 것으로 표시됩니다.

<u>재현 단계</u>:

>[!NOTE]
>
>아래 단계는 샘플 데이터를 예로 참조합니다.

1. [!UICONTROL Commerce] 관리자의 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]**(으)로 이동하여 **[!UICONTROL Display Out of Stock Products]**&#x200B;을(를) *예*(으)로 설정합니다.
1. 다시 한 번, 관리자로부터 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 제품 편집 페이지에서 구성 가능한 제품을 편집합니다(예: 샘플 데이터를 사용하는 경우 &quot;WB04&quot; SKU).
   * 구성 변형 중 하나의 경우 수량을 *0*(예: &quot;WB04-M-Purple&quot;의 경우)으로 설정합니다.
1. 이제 상점 첫 화면에서 구성 가능한 제품을 여십시오.
1. 재고가 0인 구성 가능한 변형의 제품 크기(즉, &quot;M&quot;)를 선택합니다.

<u>예상 결과</u>:

품절 옵션이 비활성화되어 [!UICONTROL Out of Stock](으)로 표시되었습니다.

<u>실제 결과</u>:

[!UICONTROL Out of Stock]인 색상 견본을 포함하여 모든 색상 견본이 활성화됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
