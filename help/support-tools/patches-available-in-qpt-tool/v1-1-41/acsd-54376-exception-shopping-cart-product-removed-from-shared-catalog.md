---
title: 'ACSD-54376: [!UICONTROL shared catalog]에서 제품을 제거할 때 장바구니에 예외가 발생했습니다.'
description: ACSD-54376 패치를 적용하여 장바구니에 제품을 추가한 후 [!UICONTROL shared catalog]에서 제품을 제거할 때 장바구니에서 예외가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: [!UICONTROL shared catalog]에서 제품을 제거할 때 장바구니에 예외가 발생했습니다.

ACSD-54376 패치는 장바구니에 제품을 추가한 후 [!UICONTROL shared catalog]에서 제품을 제거할 때 장바구니에서 예외가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54376입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품을 장바구니에 추가한 후 [!UICONTROL shared catalog]에서 제거하면 장바구니에서 예외가 발생합니다.

<u>재현 단계</u>:

1. B2B와 함께 Adobe Commerce을 설치합니다.
1. [!UICONTROL shared catalog] 사용
1. 제품을 만들어 기본 [!UICONTROL shared catalog]에 할당합니다.
1. 상점 첫 화면에서 장바구니에 제품을 추가합니다.
1. [!UICONTROL shared catalog]에서 제품을 제거합니다.
1. 미니 장바구니 드롭다운을 사용하여 체크아웃 페이지로 이동합니다.

<u>예상 결과</u>:

예외는 처리되며 사용자에게 표시되지 않습니다.

<u>실제 결과</u>:

처리되지 않은 예외가 체크아웃 페이지에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
