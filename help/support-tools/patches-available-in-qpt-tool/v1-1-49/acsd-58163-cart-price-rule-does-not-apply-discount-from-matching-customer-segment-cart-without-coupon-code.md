---
title: 'ACSD-58163: [!UICONTROL Cart Price Rule]은(는) 쿠폰 코드 없이 일치하는 [!UICONTROL Customer Segment] 장바구니에서 할인을 적용하지 않습니다.'
description: ACSD-58163 패치를 적용하여 [!UICONTROL Cart Price Rule]이(가) 쿠폰 코드가 없는 일치하는 [!UICONTROL Customer Segment] 장바구니에서 게스트에 대한 할인을 적용하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
source-git-commit: 7603a482953dc0ac0784ab6e6d3b22e4245e3e75
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-58163: [!UICONTROL Cart Price Rule]은(는) 쿠폰 코드가 없는 일치하는 [!UICONTROL Customer Segment] 장바구니에서 할인을 적용하지 않습니다.

ACSD-58163 패치는 [!UICONTROL Cart Price Rule]이(가) 쿠폰 코드 없이 일치하는 [!UICONTROL Customer Segment] 장바구니에서 할인을 적용하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58163입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Cart Price Rule]은(는) 쿠폰 코드가 없는 일치하는 [!UICONTROL Customer Segment] 장바구니에서 게스트에 대한 할인을 적용하지 않습니다.

<u>재현 단계</u>:

1. 고객 세그먼트 만들기:
   * 방문자용.
   * 장바구니에 한 개의 제품이 있는 조건 포함.

1. *[!UICONTROL Cart Price Rule]* 만들기:
   * 쿠폰 코드가 없습니다.
   * 방문자 고객 세그먼트와 일치하는 조건 포함.

1. 간단한 제품을 만듭니다.
1. 상점을 게스트로 엽니다.
1. 간단한 제품 하나를 장바구니에 추가합니다.
1. 장바구니로 이동합니다.

<u>예상 결과</u>:

*[!UICONTROL Cart Price Rule]* 할인이 적용됩니다.

<u>실제 결과</u>:

*[!UICONTROL Cart Price Rule]* 할인이 적용되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
