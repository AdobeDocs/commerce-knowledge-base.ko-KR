---
title: 'MDVA-30284 패치: Elasticsearch 7 - 인덱스의 총 필드 [XXXXX]에 대한 제한이 초과되었습니다.'
description: MDVA-30284 패치는 Elasticsearch 7을 사용할 때 "인덱스의 총 필드 수 제한 \[XXXXX\]이(가) 초과되었습니다"라는 오류 메시지가 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-30284입니다.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-30284 패치: Elasticsearch 7 - 인덱스에서 총 필드 [XXXXX]의 제한을 초과했습니다.

MDVA-30284 패치는 Elasticsearch 7을 사용할 때 &quot;인덱스의 총 필드 수 제한 \[XXXXX\]이(가) 초과되었습니다&quot;라는 오류 메시지가 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-30284입니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.5-p2의 Adobe Commerce용으로 설계되었습니다
* Elasticsearch 7은 Adobe Commerce 2.3.5 및 2.4.x와 호환됩니다

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Elasticsearch 필드 제한이 잘못되어 \[catalogsearch\_fulltext\] 인덱서를 실행할 때 다음 오류가 발생합니다.

*인덱스 [xxxxxx]의 총 필드 [xxx] 제한이 초과되었습니다*

이 문제는 제품 속성이 많을 때 발생합니다. 이 문제는 Elasticsearch이 필드 수를 계산하는 방식에 의해 트리거됩니다. 필드에 할당된 특성이 있는 경우 이러한 필드가 별도의 인덱서로 인덱싱되는 경우가 있습니다. 이로 인해 제한 초과 경고가 발생합니다.

<u>재현 단계:</u>

<u>필수 구성 요소</u>

* module-elasticsearch 100.3.5가 설치되었습니다.
* Elasticsearch 7이 설치되었습니다.
* Elasticsearch을 검색 백엔드로 설정합니다.

1. 제품에 대해 1000개 이상의 속성을 만듭니다.
1. 각 패밀리에 대한 제품을 만듭니다.
1. 인덱서를 실행합니다.

<u>예상 결과:</u>

모든 제품은 Elasticsearch 색인에서 사용할 수 있습니다.

<u>실제 결과:</u>

1. Elasticsearch 오류:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. 새 제품이 색인화되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
