---
title: 'MDVA-34665: 번들 제품이 상점 카테고리 페이지 사라짐'
description: MDVA-34665 패치는 범주 페이지에 번들 제품이 누락된 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-34665입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665: 번들 제품이 상점 카테고리 페이지 사라짐

MDVA-34665 패치는 범주 페이지에 번들 제품이 누락된 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-34665입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.4-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.4-2.3.4-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**사례 1:**

<u>필수 구성 요소</u>:

1. 하나의 간단한 제품을 번들 옵션으로 사용하여 15,000개의 번들 제품을 만듭니다. 여러 개의 번들 제품에 동일한 간단한 제품을 사용하지 마십시오.
1. 간단한 제품은 *개별적으로 표시되지 않음*(으)로 설정해야 합니다.

<u>재현 단계</u>:

1. 15k 번들 제품을 각각 7,500개씩 두 개의 카테고리로 할당합니다.
1. 모든 간단한 제품 (15k)을 선택하고 제품 일괄 속성 업데이트를 사용하여 재고를 업데이트합니다. 우리의 목표는 검색 cl 테이블에 많은 ID를 갖는 것입니다(cl 테이블은 인덱서가 업데이트해야 하는 레코드를 알기 위해 사용하는 테이블임).
1. `catalogsearch_fulltext_cl` 테이블에 15K ID가 있는지 확인하십시오.
1. `indexer_update_all_views` 인덱서가 실행되었는지 확인하십시오.
1. 카테고리 페이지를 지속적으로 쿼리하고 제품 수를 관찰합니다.

<u>예상 결과</u>:

제품 수는 리인덱싱 후에도 그대로 유지되어야 합니다.

<u>실제 결과</u>:

잠시 후 제품 수가 7,450개로 감소합니다. 지수화가 끝난 후에도 7,450개 안에 남아 있다.

**사례 2:**

<u>재현 단계</u>:

1. 연결된 단순 제품을 옵션으로 사용하여 번들 제품을 만듭니다.
1. 인덱서 모드를 *일정에 따라 업데이트*(으)로 변경하십시오.
1. 번들 제품을 카테고리에 할당합니다.
1. 단순 제품의 재고 상태를 *재고 부족*(으)로 변경합니다.
1. cron을 실행하십시오. 번들 제품이 상점 앞에서 사라집니다.
1. 간단한 제품에 재고를 추가하고 저장합니다.
1. cron indexer를 실행합니다.
1. 카테고리 페이지를 새로 고칩니다.

<u>예상 결과</u>:

그 제품은 아직 없습니다.

<u>실제 결과</u>:

번들 제품이 다시 나타납니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
