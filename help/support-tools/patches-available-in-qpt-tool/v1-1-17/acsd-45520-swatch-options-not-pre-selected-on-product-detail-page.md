---
title: 'ACSD-45520: 제품 세부 사항 페이지에서 견본 옵션이 선택되지 않음'
description: ACSD-45520 패치는 사용자가 장바구니에서 구성 가능한 제품을 편집할 때 제품 세부 사항 페이지에서 견본 옵션이 사전 선택되지 않는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45520입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: 941f4a45-bc3c-44c0-a582-ddfe179fa8c3
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-45520: 제품 세부 사항 페이지에서 견본 옵션이 선택되지 않음

ACSD-45520 패치는 사용자가 장바구니에서 구성 가능한 제품을 편집할 때 제품 세부 사항 페이지에서 견본 옵션이 사전 선택되지 않는 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45520입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 장바구니에서 구성 가능한 제품을 편집할 때 제품 세부 사항 페이지에서 견본 옵션이 선택되어 있지 않습니다.

<u>재현 단계</u>:

1. 제품 옵션(예: 색상)을 사용하여 구성 가능한 제품을 만듭니다.
1. 구성 가능한 제품을 장바구니에 추가합니다.
1. 내 장바구니 페이지로 이동합니다.
1. 1단계에서 추가한 구성 가능한 제품에서 편집 단추를 클릭합니다.
1. 편집 페이지의 제품 옵션을 확인합니다.

<u>예상 결과</u>:

제품 옵션이 선택되어 있습니다.

<u>실제 결과</u>:

제품 옵션이 선택되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
