---
title: 'ACSD-51735: 제품 재고가 0일 때 주문 항목 상태가 *[!UICONTROL Ordered]*(으)로 잘못 설정됨'
description: ACSD-51735 패치를 적용하여 제품 재고가 0일 때 주문 항목 상태가 *[!UICONTROL Ordered]*(으)로 잘못 설정되는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: 제품 재고가 0일 때 주문 항목 상태가 *[!UICONTROL Ordered]*(으)로 잘못 설정됨

ACSD-51735 패치는 제품 재고가 0일 때 주문 항목 상태가 *[!UICONTROL Ordered]*(으)로 잘못 설정되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-50895입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 재고가 0일 때 주문 항목 상태가 *[!UICONTROL Ordered]*(으)로 잘못 설정되었습니다.

<u>필수 구성 요소</u>:

* Adobe Commerce Inventory management(MSI) 모듈이 설치되었습니다.
* **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**&#x200B;에서 하위 주문이 활성화됩니다.

<u>재현 단계</u>:

1. 새 재고를 생성합니다.
1. 새 소스를 만듭니다.
1. 기본 웹 사이트를 신규 재고에 지정하고 신규 출처를 지정합니다.
1. 새 제품을 만듭니다.

   * 기본 출처 수량을 10으로 설정하고 신규 출처 수량을 0으로 설정합니다.

1. 상점 앞의 장바구니에 제품을 추가합니다.
1. 체크아웃 시 제품이 새 출처에서 오더됨을 나타내는 미납 주문 경고를 확인합니다.
1. 주문하십시오.
1. Admin에서 주문을 열고 미납 주문 상태를 확인합니다.

<u>예상 결과</u>:

주문에 따르면 수량 1은 미납주문된 것입니다.

<u>실제 결과</u>:

주문에는 수량 1이 미납주문된 것이 아니라 주문된 것으로 표시됩니다.

>[!MORELIKETHIS]
>
>[주문 항목 상태가 *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)(으)로 잘못 설정됨

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
