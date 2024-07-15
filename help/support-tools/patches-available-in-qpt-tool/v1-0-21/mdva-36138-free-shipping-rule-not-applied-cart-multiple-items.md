---
title: 'MDVA-36138: 무료 배송 규칙이 장바구니 여러 항목에 적용되지 않음'
description: MDVA-36138 패치는 장바구니에 여러 항목이 있는 경우 무료 배송의 일치하는 SKU가 무료 배송을 적용하지 못하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36138입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138: 무료 배송 규칙이 장바구니 여러 항목에 적용되지 않음

MDVA-36138 패치는 장바구니에 여러 항목이 있는 경우 무료 배송의 일치하는 SKU가 무료 배송을 적용하지 못하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-36138입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.4

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.2 이상

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 품목에만 무료배송 규칙을 적용하면 장바구니에 다른 품목이 있는 경우에는 할인이 적용되지 않는다.

<u>재현 단계</u>:

1. 단순 제품(simple1 및 simple2)을 만듭니다.
1. USPS(또는 모든 온라인 배송 방법)를 구성합니다.

   * 허용된 방법: 우선 순위 메일(장바구니와 체크아웃에 긴 방법 목록을 포함하지 않기 위해 선택한 방법).
   * 무료 방법: 우선 순위 메일.

1. 장바구니 규칙을 만듭니다.

   * 쿠폰 코드 지정
   * 조건 탭: 비워 둠
   * 작업 탭:

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. simple1을 장바구니에 추가합니다.
1. 쿠폰 코드를 적용합니다.
1. 간단 2를 장바구니에 추가합니다.

<u>예상 결과</u>:

* simple1 - 무료 배송이 있어야 합니다.
* simple2 - 배송비를 지불해야 합니다.

<u>실제 결과</u>:

배송비에는 simple1과 simple2가 포함되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
