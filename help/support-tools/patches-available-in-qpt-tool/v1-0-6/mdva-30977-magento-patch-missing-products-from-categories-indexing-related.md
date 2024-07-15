---
title: 'MDVA-30977: 범주에 제품 누락, 관련 색인화'
description: MDVA-30977 패치는 많은 수의 제품을 사용하여 색인 재지정 또는 대량 작업을 수행하는 동안 상점 카테고리 페이지에 표시되는 제품과 관련된 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정될 예정입니다.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977: 범주에 제품 누락, 관련 색인화

MDVA-30977 패치는 많은 수의 제품을 사용하여 색인 재지정 또는 대량 작업을 수행하는 동안 상점 카테고리 페이지에 표시되는 제품과 관련된 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

이 패치는 클라우드 인프라 2.3.4의 Adobe Commerce에 대해 생성되었습니다. Adobe Commerce 온-프레미스 2.3.4와도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

### 문제 1

대량 제품 업데이트 시 각 페이지가 다시 로드되면 상점 내 카테고리 페이지에 표시되는 제품 수가 달라집니다.

<u>재현 단계:</u>

1. 두 개의 카테고리(각 카테고리에 있는 제품 15000개 이상)에 최소한 30000개의 제품을 만드십시오.
1. Commerce 관리자의 **카탈로그** > **제품**(으)로 이동합니다.
1. 그리드에서 모든 제품을 선택하고 일괄 속성 갱신을 수행합니다. 예를 들어 **New** = *Yes* 특성을 설정합니다.
1. `bin/magento cron:run` 명령을 사용하여 Magento cron 작업을 두 번 실행합니다.
1. Adobe Commerce에서 30000 제품 업데이트를 수행하는 동안 Storefront의 카테고리 페이지를 새로 고칩니다.

<u>예상 결과:</u>

범주의 제품 수는 각 범주 페이지를 새로 고칠 때마다 항상 15000.

<u>실제 결과:</u>

카테고리 페이지 새로 고침마다 카테고리의 제품 수가 다릅니다.

### 문제 2

인벤토리의 전체 색인 재지정이 실행되면 범주 페이지가 비어 있고 *선택 항목과 일치하는 제품을 찾을 수 없습니다* 메시지가 표시됩니다.

<u>재현 단계:</u>

1. Elasticsearch으로 Adobe Commerce을 구성합니다.
1. 새 웹 사이트를 추가합니다.
1. 새 소스를 만들고 재고 관리를 사용하여 새 웹 사이트에 할당합니다.
1. 구성 30000 제품을 만듭니다.
1. 모든 제품을 새 웹 사이트에 할당하고 새 재고 출처에 재고를 추가합니다.
1. 전체 색인 재지정을 실행합니다.
1. `bin/magento indexer:reindex inventory`을(를) 실행하여 인벤토리 색인 재지정 실행
1. 제품 수가 많은 카테고리를 찾아봅니다.

<u>예상 결과:</u>

색인 재지정 중 카테고리 페이지에 평소대로 제품이 표시됩니다.

<u>실제 결과:</u>

색인 재지정 중에 범주 페이지가 비어 있게 됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
