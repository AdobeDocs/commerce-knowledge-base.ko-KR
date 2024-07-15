---
title: 'MDVA-30428: 위시리스트가 Inventory management에서 작동하지 않음'
description: MDVA-30428 패치는 Inventory management(MSI)에서 작동하지 않는 위시리스트를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우 사용할 수 있습니다.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428: 위시리스트가 Inventory management에서 작동하지 않음

MDVA-30428 패치는 Inventory management(MSI)에서 작동하지 않는 위시리스트를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3 - 2.3.3-p1(QPT 1.0.6) 및 2.3.5 - 2.4.1(QPT 1.0.5)

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

위시리스트에 제품을 추가할 때 제품이 사용자 지정 인벤토리 소스에 할당되면 다음 메시지에 &quot;*항목을 지금 위시리스트에 추가할 수 없습니다. 위시리스트에 재고가 없으면 제품을 추가할 수 없습니다.*&quot;라는 메시지가 표시됩니다.

<u>재현 단계</u>:

1. Commerce 관리자에서 새 인벤토리 소스를 만듭니다. 단계는 사용 안내서에서 [카탈로그 > 새 Source 추가](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source)를 참조하십시오.
1. Commerce 관리자에서 새 재고 목록을 만들고 새 소스 및 기본 웹 사이트를 새 재고에 할당합니다. 단계는 사용 안내서의 [카탈로그 > 새 재고 추가](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock)를 참조하십시오.
1. 간단한 제품을 만들고 새 재고만 재고로 할당합니다.
1. 프론트엔드의 간단한 제품 세부 사항 페이지를 방문하십시오.
1. 위시리스트에 제품을 추가합니다. 다음 오류가 표시됩니다. *항목을 지금 위시리스트에 추가할 수 없습니다. 위시리스트에 재고가 없으면 제품을 추가할 수 없습니다*.

<u>예상 결과</u>:

제품은 사용자 정의 스톡으로 위시리스트에 추가해야 합니다.

<u>실제 결과</u>:

제품이 위시리스트에 추가되지 않고 오류 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
