---
title: "ACSD-46581: 장바구니에서 국가를 선택한 후 예상 총 세액이 업데이트되지 않음"
description: 장바구니에서 국가를 전환한 후 세율이 업데이트되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-46581 패치를 적용합니다.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581: 장바구니에서 국가를 선택한 후 예상 총 세액이 업데이트되지 않음

이 ACSD-46581 패치는 장바구니에서 국가를 전환한 후 세율이 업데이트되지 않는 문제를 해결합니다. 배송 방법을 선택한 후에만 업데이트됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46581입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.1-p1

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에서 국가를 전환한 후에는 세율이 업데이트되지 않습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리에서 **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**(으)로 이동합니다.
1. **[!UICONTROL Country]** = _미국_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_&#x200B;에 대한 새 세율을 만듭니다.
1. **[!UICONTROL Country]** = _인도_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_&#x200B;에 대한 새 세율을 만듭니다.
1. 미국과 인도의 두 세율을 모두 포함하는 세금 규칙을 생성합니다.
1. **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]**(으)로 이동하여 둘 이상의 배송 방법을 활성화하십시오(예: _정액 요금_ 및 _무료 배송_).
1. **[!UICONTROL Taxable Goods]** 세금 등급으로 간단한 제품을 만드십시오.
1. 매장 앞의 장바구니에 제품을 추가합니다.
1. 장바구니를 열고 세액을 확인합니다.
1. 미국에 대한 기본 세금 설정이 적용되며 세금은 8.25%의 세율을 기준으로 계산됩니다.
1. 그 나라를 인도로 바꾸다.

<u>예상 결과</u>:

인도로 전환할 때 세액이 10%로 바뀌었다.

<u>실제 결과</u>:

장바구니의 전체 구간에서는 세액이 동일하게 유지됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 자세한 내용은 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
