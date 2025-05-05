---
title: "ACSD-52736: [!UICONTROL Cart Price Rule]이(가) 예상대로 작동하지 않습니다."
description: 구성 가능한 제품 수량에 대한 요구 사항이 포함된 [!UICONTROL Cart Price Rule]이(가) 예상대로 작동하지 않는 Adobe Commerce 문제를 해결하려면 ACSD-52736 패치를 적용하십시오.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule]이(가) 예상대로 작동하지 않습니다.

ACSD-52736 패치는 구성 가능한 제품 수량에 대한 요구 사항을 포함하는 [!UICONTROL Cart Price Rule]이(가) 예상대로 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52736입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품 수량에 대한 요구 사항이 포함된 [!UICONTROL Cart Price Rule]이(가) 예상대로 작동하지 않습니다.

<u>재현 단계</u>:

1. 장바구니 규칙을 만듭니다.
   * [!UICONTROL Apply] = 제품 가격 할인의 백분율
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * 다음 조건과 일치하는 장바구니 항목에만 규칙을 적용합니다. 장바구니 수량은 1입니다.
2. [!UICONTROL Qty] = 2인 제품을 장바구니에 추가합니다.
3. 장바구니 가격을 확인하십시오.

<u>예상 결과</u>:

장바구니에 있는 제품의 수량이 *2*&#x200B;이므로 규칙이 적용되지 않습니다.

<u>실제 결과</u>:

할인이 적용됩니다

패치 설치 후 필요한 <u>개의 추가 단계</u>:

패치를 적용한 후 *Quantity* 특성을 사용하는 장바구니 규칙 조건을 제거하고 다시 추가해야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
