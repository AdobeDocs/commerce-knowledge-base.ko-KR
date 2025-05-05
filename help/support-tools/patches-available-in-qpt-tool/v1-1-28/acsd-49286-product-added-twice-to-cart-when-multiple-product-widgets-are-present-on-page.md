---
title: 'ACSD-49286: 여러 제품 위젯이 있는 경우 장바구니에 제품이 두 번 추가되었습니다.'
description: ACSD-49286 패치를 적용하여 페이지에 여러 제품 위젯이 있을 때 제품이 장바구니에 두 번 추가되는 Adobe Commerce 문제를 수정합니다.
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286: 여러 제품 위젯이 있는 경우 장바구니에 제품이 두 번 추가되었습니다.

ACSD-49286 패치는 페이지에 여러 제품 위젯이 있을 때 제품이 장바구니에 두 번 추가되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49286입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

페이지에 여러 제품 위젯이 있는 경우 제품이 장바구니에 두 번 추가됩니다.

<u>재현 단계</u>:

1. 관리자에 로그인하고 **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**(으)로 이동합니다.
1. 콘텐츠 섹션에서 [!DNL Page Builder]을(를) 사용하여 **[!UICONTROL Edit]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Content]**&#x200B;에 두 개의 행 요소를 추가합니다.
1. 두 행 요소에 제품을 추가합니다.
1. 첫 번째 행에서 제품 모양을 [!UICONTROL Product Grid] (으)로 설정하고 표시할 카테고리를 선택합니다.
1. 두 번째 행에서 제품 모양을 [!UICONTROL Product Carousel] (으)로 설정하고 표시할 다른 범주를 선택합니다.
1. 상점 **[!UICONTROL Home Page]**(으)로 이동하여 제품 그리드에서 제품 하나를 추가합니다.
1. [!UICONTROL Product Carousel]에서 다른 제품을 추가합니다.

<u>예상 결과</u>:

[!UICONTROL Product Grid]에서 장바구니에 제품을 추가한 후 제품 수량을 두 배로 늘리면 안 됩니다.

<u>실제 결과</u>:

[!UICONTROL Product Grid]에서 장바구니에 제품을 추가한 후 제품 수량이 두 배가 됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html). 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
