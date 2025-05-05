---
title: 'MDVA-41139: 구성 가능한 제품이 제품 가져오기 후 품절 상태가 됨'
description: MDVA-41139 패치는 구성 가능한 제품의 소스 중 하나에 대해 단순 제품의 수량 = 0일 때 제품 가져오기 후 해당 제품의 재고가 부족한 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41139입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: e90ab578-50b9-4bc4-baf9-de4182e700ae
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-41139: 구성 가능한 제품이 제품 가져오기 후 품절 상태가 됨

MDVA-41139 패치는 구성 가능한 제품의 소스 중 하나에 대해 단순 제품의 수량 = 0일 때 제품 가져오기 후 해당 제품의 재고가 부족한 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41139입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품은 제품 가져오기 후 해당 소스 중 하나에 대해 단순 제품의 수량이 0일 때 품절 상태가 됩니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 새 소스 및 스톡을 만듭니다.
1. 기본 소스 및 새 소스에 할당된 하위 제품으로 구성 가능한 제품을 만듭니다.
1. 각 하위 제품 = 0에 대해 기본 재고 값을 설정하고, 다른 재고 = 0보다 큰 경우 기본 재고 값을 설정합니다.
1. 구성 가능한 제품이 재고에 있습니다.
1. 이 제품을 내보내고 다시 가져옵니다.

<u>예상 결과</u>:

두 번째 출처의 수량이 0을 초과하여 구성 가능한 제품이 재고에 있습니다.

<u>실제 결과</u>:

구성 가능한 제품의 재고가 부족합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
