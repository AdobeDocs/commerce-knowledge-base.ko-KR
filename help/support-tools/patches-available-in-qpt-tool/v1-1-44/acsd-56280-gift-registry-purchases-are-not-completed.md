---
title: 'ACSD-56280: 선물 등록 구매가 완료되지 않음'
description: ACSD-56280 패치를 적용하여 선물 레지스트리 구입이 완료되지 않은 Adobe Commerce 문제를 해결합니다
feature: Checkout
role: Admin
exl-id: 8e78ea1d-bd55-49d7-9d74-748b8f90e28c
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-56280: 선물 등록 구매가 완료되지 않았습니다.

ACSD-56280 패치는 선물 레지스트리 구입이 완료되지 않은 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56280입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

선물 등록 구매가 완료되지 않았습니다.

<u>재현 단계</u>:

1. 고객으로 로그인한 다음 선물 레지스트리에 **[!UICONTROL product]**&#x200B;을(를) 추가합니다.
1. 선물 등록 링크를 공유합니다.
1. 다른 브라우저/시크릿 창에서 선물 등록 링크를 엽니다.
1. 수량을 추가하고 품목을 장바구니에 추가합니다.
1. **[!UICONTROL Checkout Page]**(으)로 이동하여 **[!UICONTROL shipping method]**&#x200B;을(를) 선택합니다(등록자가 제공한 배송 주소가 이미 선택되었으므로).
1. 결제 방법을 선택합니다.
1. 주문 버튼을 클릭합니다.

<u>예상 결과</u>:

주문을 해야 합니다.

<u>실제 결과</u>:

순서가 지정되지 않았으며 표시되는 오류는 `Call to a member function getUpdatedQty() on null`입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
