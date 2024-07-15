---
title: 'MDVA-37068: 가상 제품에 대한 체크아웃에 잘못된 세금이 표시됨'
description: MDVA-37068 패치는 Checkout Page에 가상 제품에 대한 잘못된 세율이 표시되면 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37068입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068: 가상 제품에 대한 체크아웃에 잘못된 세금이 표시됨

MDVA-37068 패치는 Checkout Page에 가상 제품에 대한 잘못된 세율이 표시되면 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37068입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**
Adobe Commerce(모든 배포 방법) 2.3.1-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 가상 제품만 있는 경우, 잘못된 세율이 체크아웃 페이지에 표시됩니다.

<u>필수 구성 요소</u>:

1. 두 개의 서로 다른 국가에 대해 두 개의 별도 세율 및 세금 규칙(예: 10% 및 1%)을 생성합니다.
1. 가상 제품을 만듭니다.
1. 색인 재지정 및 캐시 정리를 실행합니다.

<u>재현 단계</u>:

1. 고객을 만듭니다.
1. 다른 청구 및 배송 주소를 추가합니다.
1. 장바구니에 가상 제품을 추가합니다.
1. 장바구니 및 체크아웃 페이지를 확인합니다.

<u>예상 결과</u>:

장바구니 및 체크아웃 페이지에 표시되는 세금은 동일합니다.

<u>실제 결과</u>:

장바구니 및 체크아웃 페이지에 표시되는 세금이 동일하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
