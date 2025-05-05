---
title: 'ACSD-53118: 쿠폰이 포함된 장바구니 규칙이 제대로 작동하지 않음'
description: ACSD-53118 패치를 적용하여 장바구니의 제품에 빈 일치 속성이 있는 동안 쿠폰 코드를 사용하여 장바구니 가격 규칙이 적용되는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: a660ddb3-03fc-4460-b2a8-8e851f57e7a9
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-53118: 쿠폰이 포함된 장바구니 규칙이 제대로 작동하지 않음

ACSD-53118 패치는 장바구니의 제품에 빈 일치 속성이 있는 동안 쿠폰 코드를 사용하여 장바구니 가격 규칙이 적용되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53118입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니 가격 규칙은 장바구니에 있는 제품에 빈 일치 속성이 있는 동안 쿠폰 코드를 사용하여 적용됩니다.

<u>재현 단계</u>:

1. 가격 속성을 만들고 속성 세트에 추가합니다. 속성을 프로모션 규칙 조건에 사용할 수 있도록 합니다.
1. 제품을 만들고 새 속성을 비워 둡니다.
1. 특정 쿠폰과 다음 조건을 사용하여 장바구니 가격 규칙을 만듭니다.

   * 항목이 장바구니에서 true인 경우: Attribute1은 0입니다.

1. 2단계에서 만든 제품을 장바구니에 추가합니다.
1. 3단계에서 만든 장바구니 규칙에 대한 쿠폰 코드를 사용합니다.

<u>예상 결과</u>:

장바구니에는 할인이 적용되지 않습니다.

<u>실제 결과</u>:

장바구니에 할인이 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
