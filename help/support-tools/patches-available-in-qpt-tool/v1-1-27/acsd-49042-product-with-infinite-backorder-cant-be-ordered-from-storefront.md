---
title: "ACSD-49042: 무한 역주문의 제품은 상점에서 주문할 수 없습니다."
description: ACSD-49042 패치를 적용하여 무한 역주문이 있는 제품을 상점 전면에서 주문할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: 무한 주문된 제품은 상점에서 주문할 수 없습니다.

ACSD-49042 패치는 백오더가 무한한 제품을 상점 앞에서 주문할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49042입니다. 이 문제는 Adobe Commerce 2.4.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

백오더가 무한한 제품을 상점에서 주문할 수 없을 때 오류가 발생합니다.

<u>재현 단계</u>:

1. 다음 구성 설정을 설정합니다.
   * **[!UICONTROL Display Out of Stock Products]**&#x200B;이(가) *[!UICONTROL Yes]*(으)로 설정되었습니다.
   * **[!UICONTROL Backorders]**&#x200B;이(가) *[!UICONTROL Allow Qty Below 0]*(으)로 설정되었습니다.
1. 새 **[!DNL custom stock]** 및 **[!DNL custom source]**&#x200B;을(를) 추가합니다.
1. **[!DNL custom source]**&#x200B;에 제품을 할당하고 재고 번호가 설정되어 있는지 확인하십시오(예: *10*).
1. 제품 편집 페이지에서 **[!UICONTROL Advanced Inventory]**&#x200B;을(를) 엽니다. 장바구니에서 **[!UICONTROL minimum quantity]**&#x200B;을(를) 설정합니다(예: *160*). 수량은 재고보다 많아야 한다.
1. 상점에 가셔서 예약하실 상품을 구매하세요.
1. **[!UICONTROL product quantity]**&#x200B;을(를) *0*(으)로 변경합니다. 중요한 점은 예약이 있을 때 **[!DNL Admin panel]**&#x200B;에서 제품을 저장하는 것입니다.
1. 상점 전면에서 **[!UICONTROL product page]**&#x200B;을(를) 열고 장바구니에 제품을 추가해 보십시오.

<u>예상 결과</u>:

*0* 이하 수량에 대한 미납주문이 허용되므로 제품을 장바구니에 추가할 수 있습니다.

<u>실제 결과</u>:

그 상품은 품절로 진열되어 있다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
