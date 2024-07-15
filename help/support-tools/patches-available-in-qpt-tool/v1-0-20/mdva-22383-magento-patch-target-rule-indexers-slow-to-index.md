---
title: 'MDVA-22383: 대상 규칙 인덱서가 인덱싱할 때 느림'
description: MDVA-22383 패치를 사용하면 제품/Target 규칙 및 Target 규칙/Product 인덱서를 다시 인덱싱하는 데 시간이 너무 오래 걸리는 문제가 해결됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-22383입니다. 이 문제는 Adobe Commerce 2.3.5에서 해결되었습니다.
exl-id: fbf28983-5883-4769-90bd-1c97c2b2e2b8
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-22383: 대상 규칙 인덱서가 인덱싱할 때 느림

MDVA-22383 패치를 사용하면 제품/Target 규칙 및 Target 규칙/Product 인덱서를 다시 인덱싱하는 데 시간이 너무 오래 걸리는 문제가 해결됩니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-22383입니다. 이 문제는 Adobe Commerce 2.3.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.3.2의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0-2.3.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품/Target 규칙 및 Target 규칙/제품 인덱서를 다시 인덱싱하는 데 시간이 너무 오래 걸립니다.

<u>필수 구성 요소:</u> 제품이 많으면 문제가 발생합니다.

<u>재현 단계:</u>

1. 제품과 함께 대상 규칙을 만들어 조건에 일치시키고 조건이 컬렉션에 제품을 더 추가해야 하며 속성(카테고리 또는 속성 집합이 아님)을 가져야 합니다.
1. 다음 명령을 실행합니다.

   ```bash
       bin/magento indexer:reindex targetrule_product_rule
   ```

<u>실제 결과:</u>

리인덱싱이 중단되었습니다. 제품 저장이 중단되었습니다.

<u>예상 결과:</u>

리인덱싱이 완료되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
