---
title: 'MDVA-41139: 구성 가능한 제품이 제품 가져오기 후 품절 상태가 됨'
description: MDVA-41139 패치는 구성 가능한 제품의 소스 중 하나에 대해 단순 제품의 수량 = 0일 때 제품 가져오기 후 해당 제품의 재고가 부족한 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41139입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: e90ab578-50b9-4bc4-baf9-de4182e700ae
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-41139: 구성 가능한 제품이 제품 가져오기 후 품절 상태가 됨

MDVA-41139 패치는 구성 가능한 제품의 소스 중 하나에 대해 단순 제품의 수량 = 0일 때 제품 가져오기 후 해당 제품의 재고가 부족한 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치되었습니다. 패치 ID는 MDVA-41139입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품은 제품 가져오기 후 해당 소스 중 하나에 대해 단순 제품의 수량이 0일 때 품절 상태가 됩니다.

<u>전제 조건</u>:

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

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
