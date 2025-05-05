---
title: 'ACSD-48044: 여러 기프트 카드를 적용하면 주문이 실행되지 않음'
description: ACSD-48044 패치를 적용하여 여러 배송이 있는 단일 주문에 여러 기프트 카드를 적용하면 주문이 이루어지지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: fe57063c-d69c-4b80-a59c-912c2603f6af
feature: Admin Workspace, Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-48044: 여러 기프트 카드를 적용하면 주문이 실행되지 않습니다.

ACSD-48044 패치는 여러 배송이 있는 단일 주문에 여러 기프트 카드를 적용하면 주문이 이루어지지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-48044입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

멀티배송이 가능한 단일 주문에 여러 상품권을 적용하면 주문이 이뤄지지 않는다.

<u>재현 단계</u>:

1. Adobe Commerce의 클린 버전을 설치합니다.
1. 가격이 $100인 간단한 제품과 $10인 간단한 제품을 만듭니다.
1. [!UICONTROL Admin panel]에 로그인하고 기프트 카드 두 장을 만듭니다.

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = $25

1. 두 개의 주소로 고객을 만듭니다.
1. 장바구니에 두 제품을 추가합니다.

   * 먼저 $10 제품을 추가한 다음 $100 제품을 추가합니다. $100 제품이 먼저 추가되면 문제를 재현할 수 없습니다.

1. 장바구니로 이동하여 만든 두 개의 기프트 카드를 추가합니다.
1. 장바구니 페이지에서 **[!UICONTROL Ship to Multiple Addresses]**&#x200B;을(를) 클릭합니다.
1. 각 제품을 다른 주소에 할당합니다.
1. **[!UICONTROL Shipping information]** 페이지로 이동합니다.
1. **[!UICONTROL Billing information]** 페이지로 이동합니다.
1. 문제를 확인할 수 있는 **[!UICONTROL Review Your Order]** 페이지로 이동합니다.
1. 주문해 보세요.

<u>예상 결과</u>:

* 기프트 카드는 총액에 정확하게 적용됩니다.
* 주문이 완료되었습니다.

<u>실제 결과</u>:

기프트 카드 금액이 *오류와 혼합되어 있습니다. 기프트 카드 코드를 수정하십시오.*&#x200B;을(를) 주문합니다.

* 첫 번째 제품:

   * 기프트 카드 제거 (00GXM6SUGBLW) - $15.00
   * 기프트 카드 제거(02KB8M0H0GRD) - $0.00

* 두 번째 제품:

   * 기프트 카드 제거 (00GXM6SUGBLW) - $25.00
   * 기프트 카드 제거(02KB8M0H0GRD) - $35.00

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
