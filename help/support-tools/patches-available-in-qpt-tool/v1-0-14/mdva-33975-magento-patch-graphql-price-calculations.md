---
title: 'MDVA-33975 패치: GraphQL 가격 계산'
description: 'MDVA-33975 패치는 GraphQL 가격 계산 문제를 해결합니다. 이러한 문제는 다음과 같습니다.'
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# MDVA-33975 패치: GraphQL 가격 계산

MDVA-33975 패치는 GraphQL 가격 계산 문제를 해결합니다. 이러한 문제에는 다음이 포함됩니다.

* 카탈로그 가격 규칙이 특정 고객 그룹에 적용되면 장바구니에 있는 항목의 가격과 주문 합계가 GraphQL에서 올바르게 계산되지 않습니다.
* 카탈로그 가격 규칙이 API의 `CartItemPrices`에 포함되어 있지 않습니다.
* 일반 고객의 고객 그룹 가격은 GraphQL 제품 쿼리 응답에 추가되지 않습니다.
* 견적 가격에 대한 응답을 제공하기 전에 견적 합계를 다시 계산하면 적용된 규칙이 손실됩니다.
* 마지막 청구 단계에서 배송 금액 할인이 검색되지 않았고, 총계가 잘못 표시되었습니다.
* 고객 세그먼트가 장바구니 가격 규칙 조건에서 사용되는 경우 GraphQL에서 할인이 적용되지 않습니다.

이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14가 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* 이 패치는 Adobe Commerce 온-프레미스 2.4.1용으로 설계되었습니다.
* 이 패치는 Adobe Commerce 버전인 Adobe Commerce 온프레미스 및 Adobe Commerce on cloud infrastructure 2.3.4 - 2.4.1과도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
