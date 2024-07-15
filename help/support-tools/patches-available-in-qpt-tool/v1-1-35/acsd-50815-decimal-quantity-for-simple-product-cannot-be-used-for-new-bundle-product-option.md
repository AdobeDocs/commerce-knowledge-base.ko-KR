---
title: 'ACSD-50815: 단순 제품의 10진수 수량은 새 번들 제품 옵션에 사용할 수 없습니다.'
description: ACSD-50815 패치를 적용하여 단순 제품의 10진수 수량을 새 번들 제품 옵션에 사용할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin
exl-id: f4aa417c-b0eb-4a68-bf1e-fd86770cc72d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815: 단순 제품의 10진수 수량은 새 번들 제품 옵션에 사용할 수 없습니다.

ACSD-50815 패치는 단순 제품의 십진수 수량을 새 번들 제품 옵션에 사용할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-50815입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

단순 제품의 소수 수량은 새로운 번들 제품 옵션에 사용할 수 없습니다.

<u>재현 단계</u>:

1. 관리자로 로그인합니다.
1. 간단한 새 제품을 만듭니다.
   * **[!UICONTROL Advanced Inventory]** 창에서 [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes]을(를) 설정합니다.
   * 간단한 제품을 저장합니다.
1. 새 번들 제품을 만듭니다.
1. 옵션을 추가합니다.
1. 이 옵션에 간단한 제품을 추가합니다.
1. 번들 제품 옵션에서 간단한 제품에 대한 10진수를 설정하십시오. 예를 들어 1.5입니다.

<u>예상 결과</u>:

십진법 수량을 설정하는 것은 가능합니다. 오류가 표시되지 않습니다.

<u>실제 결과</u>:

오류 *이 필드에 올바른 숫자를 입력하십시오*&#x200B;이(가) 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
