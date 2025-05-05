---
title: 'ACSD-51204: 제품이 대변 메모를 생성한 후 재고로 반환되지 않음'
description: ACSD-51204 패치를 적용하여 대변 메모를 작성한 후 제품이 재고로 돌아오지 않는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: 제품이 대변 메모를 생성한 후 재고로 반환되지 않음

ACSD-51204 패치는 대변 메모를 작성한 후 제품이 재고로 돌아오지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51204입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

품절된 상품은 대변 메모를 작성한 후 재고가 돌아오지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Adobe Commerce]**&#x200B;을(를) 설치하고 기본 *원본* 및 *스톡*&#x200B;으로만 **[!UICONTROL Inventory Management Module]**&#x200B;을(를) 사용하도록 설정하십시오.
1. 수량이 *10*&#x200B;인 **[!UICONTROL new product]**&#x200B;을(를) 추가합니다.
1. 제품을 **[!UICONTROL default stock]**&#x200B;에 할당합니다.
1. Storefront에서 제품을 장바구니에 추가하고 전체 가용 수량 10에 대해 주문합니다.
1. 관리 패널에서 주문에 대한 *송장* 및 *배송*&#x200B;을 생성합니다.
1. 모든 항목에 대해 *재고로 돌아가기* 확인란이 선택된 **[!UICONTROL Credit Memo]**&#x200B;을(를) 만듭니다.
1. 관리자에서 제품의 **[!UICONTROL Salable Quantity]**&#x200B;을(를) 확인하십시오.

<u>예상 결과</u>:

제품의 판매 가능 수량은 *10*(으)로 반환되어야 합니다.

<u>실제 결과</u>:

제품의 판매 가능 수량이 *0*(으)로 남았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>)을 참조하세요.
