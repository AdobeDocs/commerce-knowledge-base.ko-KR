---
title: 'ACSD-47875: 재고 관리를 사용하여 스토어 보기 범위의 장바구니에 제품을 추가할 수 없음'
description: ACSD-47875 패치를 적용하여 재고 관리를 사용하는 특정 스토어 보기 범위에 대해 관리자의 고객 장바구니에 제품을 추가할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875: 재고 관리를 사용하여 스토어 보기 범위의 장바구니에 제품을 추가할 수 없음

ACSD-47875 패치는 재고 관리를 사용하는 특정 스토어 보기 범위에 대한 관리자의 고객 장바구니에 제품을 추가할 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47875입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 사용자는 MSI가 설치된 특정 스토어 보기 범위에 대해 관리자의 **[!UICONTROL Manage Shopping Cart]** 기능을 사용하여 고객 장바구니에 제품을 추가할 수 없습니다.

<u>필수 구성 요소</u>:

[!DNL Adobe Commerce Inventory Management (MSI)]개의 모듈이 설치되고 사용하도록 설정되었습니다.

<u>재현 단계</u>:

1. 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. *기본* 이외의 추가 원본을 만드십시오.
1. 새 스톡을 만들고 새 웹 사이트 및 새 소스에 할당합니다.
1. 새 웹 사이트에 대한 새 고객을 만듭니다.
1. 새 웹 사이트에만 제품을 할당하고 기본 웹 사이트에서 할당을 취소합니다.

   * 새 소스를 할당하고 새 소스에 대해 수량을 *0* 이상으로 설정하고 기본 소스에 대해 *0*&#x200B;으로 설정합니다.

1. 관리자의 **[!UICONTROL Customer Edit]** 페이지로 이동합니다. **[!UICONTROL Manage Shopping Cart]**&#x200B;을(를) 클릭합니다.
1. 스토어 보기 범위를 새 스토어 보기로 변경합니다.
1. **[!UICONTROL Products]** 섹션으로 이동하여 제품을 검색하십시오.
1. 제품을 선택하고 **[!UICONTROL Add selections to my cart]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

제품이 장바구니에 추가됩니다.

<u>실제 결과</u>:

* 다음 오류가 발생합니다. *추가하려는 제품을 사용할 수 없습니다.*
* 제품이 장바구니에 추가되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
