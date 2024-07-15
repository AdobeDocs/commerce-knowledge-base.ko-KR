---
title: 'MDVA-33382 패치: 무효화된 인덱서'
description: MDVA-33382 패치는 범주에서 제품을 추가, 제거 또는 순서 변경 후 인덱서가 무효화될 때 발생하는 문제를 해결합니다. 무효화된 인덱서는 'catalog_category_product' , 'catalogsearch_fulltext' (및 해당 종속 항목)입니다.
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# MDVA-33382 패치: 무효화된 인덱서

MDVA-33382 패치는 범주에서 제품을 추가, 제거 또는 순서 변경 후 인덱서가 무효화될 때 발생하는 문제를 해결합니다. 무효화된 인덱서는 `catalog_category_product` , `catalogsearch_fulltext`(및 해당 종속 항목)입니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** 클라우드 인프라 2.3.4-p2 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 모든 인덱스 인덱서 모드를 **일정에 따라 업데이트**(으)로 설정합니다.
1. 범주 편집 페이지에서 제품을 제거합니다.
1. 범주를 저장합니다.
1. 백엔드 또는 CLI에서 인덱스 상태를 확인합니다.

<u>예상 결과</u>:

예상대로 `catalog_category_product` , `catalogsearch_fulltext`(및 해당 종속 항목) 인덱스가 무효화되지 않습니다.

<u>실제 결과</u>:

`catalog_category_product` , `catalogsearch_fulltext` 인덱스(및 해당 종속 항목)가 무효화되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
