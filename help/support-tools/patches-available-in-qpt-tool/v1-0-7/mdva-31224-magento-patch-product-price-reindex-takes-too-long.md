---
title: 'MDVA-31224 패치: 제품 가격 다시 색인이 너무 오래 걸림'
description: MDVA-31224 패치는 제품 가격 재색인이 완료되는 데 너무 오래 걸리거나 완료되지 않을 때 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7이 설치된 경우 사용할 수 있습니다.
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# MDVA-31224 패치: 제품 가격 다시 색인이 너무 오래 걸림

MDVA-31224 패치는 제품 가격 재색인이 완료되는 데 너무 오래 걸리거나 완료되지 않을 때 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.3의 Adobe Commerce용으로 설계되었습니다.
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.3 - 2.3.4-p2와도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 가격 재색인이 완료되기까지 너무 오래 걸리거나 완료되지 않을 수 있습니다.

<u>재현 단계:</u>

1. 15가지 옵션이 포함된 6000 번들 제품을 만들 수 있습니다.
1. 30개의 옵션으로 1개의 번들 제품을 만듭니다.
1. CLI에서 가격 재인덱싱 실행:     `bin/magento indexer:reindex catalog_product_price`

<u>예상 결과:</u>

제품 가격 재지수를 완료하는 데 1.5시간 이상 걸립니다.

<u>실제 결과:</u>

제품 가격 재지수는 완료하는 데 짧은 시간(1~2분)이 소요됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
