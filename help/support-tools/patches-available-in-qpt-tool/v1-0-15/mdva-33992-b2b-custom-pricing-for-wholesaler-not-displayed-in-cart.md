---
title: 'MDVA-33992: 장바구니에 표시되지 않은 도매업체에 대한 B2B 사용자 지정 가격'
description: MDVA-33992 패치는 제품이 장바구니에 추가될 때 B2B 고객에 대한 사용자 정의 가격이 반영되지 않는 문제를 해결합니다. 이 패치는 QPT(Quality Patches Tool) 1.0.15가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992: 장바구니에 표시되지 않은 도매업체에 대한 B2B 사용자 지정 가격

MDVA-33992 패치는 제품이 장바구니에 추가될 때 B2B 고객에 대한 사용자 정의 가격이 반영되지 않는 문제를 해결합니다. 이 패치는 QPT(Quality Patches Tool) 1.0.15가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**B2B가 있는 클라우드 인프라 2.4.1의 Adobe Commerce Adobe Commerce 버전**&#x200B;에 대한 패치가 만들어졌습니다.

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0-2.4.1-p1, B2B 포함

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

B2B 고객을 위한 사용자 지정 요금은 제품이 장바구니에 추가될 때 반영되지 않습니다.

<u>재현 단계</u>:

공유 카탈로그가 활성화된 B2B 버전에서 이 문제를 재현할 수 있습니다.

1. 사용자 지정 공유 카탈로그가 할당된 B2B 회사를 만듭니다.
1. 사용자 지정 가격(계층 가격)으로 회사의 사용자 지정 카탈로그에 제품을 만듭니다.
1. B2B 고객은 사용자 지정 제품 가격이 카탈로그에 표시되는지 확인합니다.
1. B2B 고객은 제품을 장바구니에 추가합니다.

<u>예상 결과</u>:

올바른 가격이 장바구니에 표시되며 카탈로그의 가격과 일치합니다.

<u>실제 결과</u>:

사용자 지정 가격이 사라지고 기본 카탈로그의 일반 가격이 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
