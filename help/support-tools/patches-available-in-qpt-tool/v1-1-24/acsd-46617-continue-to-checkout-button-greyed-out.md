---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]** 단추는 소계가 구성된 최소 주문 수량보다 클 때 회색으로 표시됩니다.'
description: ACSD-46617 패치를 적용하여 소계가 구성된 최소 순서 양보다 큰 경우에도 **[!UICONTROL Continue to Checkout]** 단추가 회색으로 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: 소계가 &quot;[!UICONTROL Minimum Order Amount]&quot;보다 클 때 &quot;[!UICONTROL Continue to Checkout]&quot; 단추가 회색으로 표시됨

이 ACSD-46617 패치는 소계가 구성된 최소 순서 양보다 큰 경우에도 **[!UICONTROL Continue to Checkout]** 단추가 회색으로 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-46617입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

소계가 구성된 최소 주문 수량보다 큰 경우에도 **[!UICONTROL Continue to Checkout]** 단추가 회색으로 표시됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자 > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]**(으)로 이동하여 다음을 설정합니다.
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;

     [!UICONTROL Minimum Amount]: *2*

1. [!UICONTROL Cart Price Rule] 만들기
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * &#x200B;

        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. 가격이 $25인 제품을 만듭니다.
1. 제품을 장바구니에 추가합니다.
1. 장바구니로 이동하여 $5 **[!UICONTROL Flat Rate shipping]** 메서드를 선택하고 쿠폰 코드를 적용합니다.
1. 체크아웃으로 이동하여 배송을 완료하고 **[!UICONTROL Paytment]** 섹션으로 이동합니다.
1. 장바구니로 돌아갑니다.

<u>예상 결과</u>:

총 합계 $2.4가 소요량인 $2보다 많아 최소 주문량과 관련된 오류는 없다.

<u>실제 결과</u>:

* 총액 2.4달러가 최소 주문금액 2달러보다 큰 경우에도 최소 주문금액과 관련된 오류가 있다.
* **[!UICONTROL Continue to Checkout]** 단추가 회색으로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
