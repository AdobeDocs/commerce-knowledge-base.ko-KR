---
title: 'ACSD-49898: 제품 그리드에서 예외 발생'
description: ACSD-49898 패치를 적용하여 번들 제품에 1000을 초과하는 특별 가격이 있는 경우 제품 그리드에서 예외가 발생하는 Adobe Commerce 문제를 수정합니다.
exl-id: 16a0ec90-7577-46ef-aeb3-a7e9658cf64b
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898: 제품 그리드에서 예외가 발생합니다.

ACSD-49898 패치는 번들 제품에 1000을 초과하는 특별 가격이 있는 경우 제품 그리드에서 예외가 발생하는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49898입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Products 그리드는 번들 제품에 1,000을 초과하는 특별 가격이 있는 경우 예외를 발생시킵니다. 문제는 특정 로케일에서 십진수에 점 대신 쉼표를 사용하는 것과 관련이 있습니다.

<u>재현 단계</u>:

1. 번들 제품을 만듭니다.
1. 특별 가격을 9999로 설정합니다. 저장하고 닫습니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동

>[!NOTE]
>
>번들 제품 SKU가 표시되지 않는 경우 검색합니다.

<u>예상 결과</u>:

* 사용자는 특별 가격으로 번들 제품을 필터링/볼 수 있습니다.
* 특별 가격은 번들 제품의 경우 백분율로 표시되고 다른 제품 유형의 경우 가격으로 표시됩니다.

<u>실제 결과</u>:

다음 오류가 발생합니다. *숫자가 아닌 값이 발생했습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
