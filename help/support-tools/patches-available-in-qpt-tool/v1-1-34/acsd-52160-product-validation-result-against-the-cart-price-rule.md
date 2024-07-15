---
title: 'ACSD-52160: 장바구니 가격 규칙에 대한 제품 유효성 검사 결과'
description: ACSD-52160 패치를 적용하여 장바구니 가격 규칙에 대한 제품 유효성 검사 결과가 규칙 조건 *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*에 따라 제대로 평가되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160: 장바구니 가격 규칙에 대한 제품 유효성 검사 결과가 제대로 평가되지 않음

ACSD-52160 패치는 장바구니 가격 규칙에 대한 제품 유효성 검사 결과가 규칙 조건 *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;을(를) 기반으로 올바르게 평가되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52160입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니 가격 규칙에 대한 제품 유효성 검사 결과가 규칙 조건 *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;을(를) 기반으로 올바르게 평가되지 않습니다.

<u>재현 단계</u>:

1. 두 개의 다른 범주에 할당된 두 제품을 만듭니다.
1. 다음과 같은 조건으로 **[!UICONTROL Cart Price Rule]**&#x200B;을(를) 만듭니다.

   * *[!UICONTROL FOUND]* 매개 변수의 **SKU 1**
   * *[!UICONTROL NOT FOUND]* 매개 변수의 **SKU 2**

1. 장바구니에 두 제품을 모두 추가합니다.
1. 쿠폰 코드를 적용합니다.

<u>예상 결과</u>

장바구니에 제한된 범주의 제품이 포함되어 있으므로 쿠폰 코드는 적용되지 않습니다.

<u>실제 결과</u>

쿠폰 코드가 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)을 참조하세요.
