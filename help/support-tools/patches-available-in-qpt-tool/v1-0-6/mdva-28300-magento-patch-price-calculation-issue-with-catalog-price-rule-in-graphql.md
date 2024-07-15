---
title: 'MDVA-28300: GraphQL의 카탈로그 가격 규칙에 가격 계산 문제'
description: MDVA-28300 패치는 GraphQL 요청이 카탈로그 가격 규칙의 가격 변경 사항을 반영하지 않는 문제를 해결합니다. 이 패치는 QPT(Quality Patches Tool) v.1.0.6이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.3.6에서 해결되었습니다.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300: GraphQL의 카탈로그 가격 규칙에 가격 계산 문제

>[!WARNING]
>
>MDVA-33975라는 새 패치는 GraphQL 가격 계산 문제를 해결합니다. MDVA-28300은 더 이상 사용되지 않으며 MDVA-33975 패치를 적용하는 것이 좋습니다. 이 패치에 액세스하려면 [MDVA-33975: GraphQL 가격 계산](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html)을 참조하세요.

MDVA-28300 패치는 GraphQL 요청이 카탈로그 가격 규칙의 가격 변경 사항을 반영하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.3.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** Adobe Commerce 온-프레미스 2.3.5-p1

**Adobe Commerce 버전과 호환:** Adobe Commerce on-premsies 및 Adobe Commerce on cloud infrastructure 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카탈로그 가격 규칙이 특정 고객 그룹에 적용되면 장바구니의 품목 가격 및 주문 합계가 GraphQL에서 올바르게 계산되지 않습니다.

<u>재현 단계:</u>

1. 새 고객 계정을 만들고 해당 고객 그룹을 도매로 변경합니다.
1. 다음 매개 변수를 사용하여 **마케팅** > **프로모션** > **카탈로그 가격 규칙**&#x200B;에서 새 카탈로그 규칙을 만듭니다.
   * 고객 그룹: WholesaleActions:
   * 적용: *원래 항목의 백분율로 적용*
   * 할인: *50*


1. price=100인 새 제품을 만듭니다.
1. 이전에 만든 고객 계정을 사용하여 프론트엔드에 로그인합니다(이미 로그인한 경우 로그아웃한 후 다시 로그인).
1. 제품을 장바구니에 추가합니다. 제품의 가격은 50(정가 100) 및 주문 총계: 55(50 + 배송비의 5)입니다.
1. 개발자 설명서의 [customerCart 쿼리](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html)에 설명된 GraphQL API 호출을 실행합니다.

<u>예상 결과:</u>

API와 프론트엔드의 주문 합계는 동일하며 카탈로그 규칙에 의해 도입된 할인이 적용됩니다.

<u>실제 결과:</u>

주문 합계는 카탈로그 규칙 할인을 적용하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [품질 패치 도구를 사용하여 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 QPT에서 사용할 수 있는 패치 섹션을 참조하십시오.
