---
title: 'MDVA-37592: 가격이 0인 제품에 대해 가격별 정렬이 작동하지 않음'
description: MDVA-37592 Adobe Commerce 패치는 공유 카탈로그에 가격 0이 할당된 제품에 대해 가격별 정렬이 제대로 작동하지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37592입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: 가격이 0인 제품에 대해 가격별 정렬이 작동하지 않음

MDVA-37592 Adobe Commerce 패치는 공유 카탈로그에 가격 0이 할당된 제품에 대해 가격별 정렬이 제대로 작동하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37592입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce on our cloud architecture 2.4.0-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 유형) 2.3.6-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

가격 기준 정렬이 공유 카탈로그에 가격 0이 지정된 제품에 대해 제대로 작동하지 않습니다.

<u>필수 구성 요소</u>:

B2B가 설치되었습니다.

<u>재현 단계</u>:

1. 공유 카탈로그를 활성화합니다.
1. $50, $60, $70, $80와 같은 가격으로 4개의 제품을 만들어 카테고리에 할당합니다.
1. 위의 제품으로 공유 카탈로그를 만듭니다.
1. 가격이 $70인 제품에 대한 사용자 지정 가격을 0으로 설정합니다.
1. 이제 회사 사용자를 만들고 방금 만든 공유 카탈로그에 할당합니다.
1. 회사 계정을 사용하여 로그인하고 제품이 할당된 범주를 찾습니다.
1. 가격을 기준으로 정렬해 보세요.

<u>예상 결과</u>:

가격이 0인 제품은 정확하게 정렬되어 있습니다.

<u>실제 결과</u>:

가격이 0인 제품이 제대로 정렬되지 않았습니다. 대신 원래 가격에 따라 정렬됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* Adobe Commerce 온-프레미스: 개발자 설명서에서 [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 아키텍처의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
