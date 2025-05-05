---
title: 'MDVA-26005: 장바구니 가격 규칙 조건에 대한 트리에서 범주를 선택할 수 없음'
description: MDVA-26005 패치는 사용자가 장바구니 가격 규칙 조건에 대한 범주 트리에서 범주를 선택할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-26005입니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.
exl-id: d3b8efc3-fd0a-4706-8851-4cecb7d3126a
feature: Categories, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-26005: 장바구니 가격 규칙 조건에 대한 트리에서 범주를 선택할 수 없음

MDVA-26005 패치는 사용자가 장바구니 가격 규칙 조건에 대한 범주 트리에서 범주를 선택할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-26005입니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

범주 트리에서 장바구니 가격 규칙 조건에 대한 범주를 선택할 수 없습니다.

<u>재현 단계</u>:

1. 새 장바구니 가격 규칙을 만들거나 기존 장바구니 가격 규칙을 편집합니다.
1. 작업 섹션으로 이동하여 조건에서 범주를 선택합니다.
1. 카테고리 트리를 렌더링하고 카테고리를 선택해 보십시오.

<u>예상 결과</u>:

범주를 선택할 수 있습니다.

<u>실제 결과</u>:

JS 오류로 인해 범주를 선택할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
