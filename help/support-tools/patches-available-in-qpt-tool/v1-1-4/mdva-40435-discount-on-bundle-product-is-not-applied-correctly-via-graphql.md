---
title: 'MDVA-40435: GraphQL을 통해 번들 제품 할인이 올바르게 적용되지 않음'
description: MDVA-40435 패치는 GraphQL을 통해 번들 제품에 대한 할인이 올바르게 적용되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40435입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 939ba940-35b5-4ab0-81fe-38981246e389
feature: GraphQL, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-40435: GraphQL을 통해 번들 제품 할인이 올바르게 적용되지 않음

MDVA-40435 패치는 GraphQL을 통해 번들 제품에 대한 할인이 올바르게 적용되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40435입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

묶음 제품 할인은 GraphQL을 통해 올바르게 적용되지 않습니다.

<u>재현 단계</u>:

1. $5 고정 할인에 대한 쿠폰 코드가 있는 장바구니 가격 규칙을 만듭니다.
1. GraphQL을 통해 빈 장바구니를 만듭니다.
1. GraphQL을 통해 번들 제품을 장바구니에 추가합니다.
1. GraphQL을 통해 고정 금액(5$)에 대한 쿠폰 코드를 적용합니다.
1. GraphQL을 통해 장바구니 정보를 가져옵니다.

<u>예상 결과</u>:

&quot;할인&quot;은 $5입니다.

<u>실제 결과</u>:

&quot;discounts&quot;가 NULL입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
