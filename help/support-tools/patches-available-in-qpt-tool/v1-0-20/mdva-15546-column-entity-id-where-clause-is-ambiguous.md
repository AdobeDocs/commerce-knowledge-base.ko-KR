---
title: "MDVA-15546: 'entity_id' 열 where 절이 모호합니다."
description: '"MDVA-15546 패치는 일부 Amazon 확장과 관련된 성능 문제를 해결합니다. 이 문제는 예외 로그에 다음 오류로 표시됩니다. *where*   *where 절의 ''entity\\_id'' 열, 쿼리: SELECT \\`main\\\_table\\\`.\\*, \\`extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\`. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-15546입니다."'
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546: &#39;entity_id&#39; 열 where 절이 모호합니다.

MDVA-15546 패치는 일부 Amazon 확장과 관련된 성능 문제를 해결합니다. 이 문제는 예외 로그에 다음 오류로 표시됩니다. *where*   *where 절이 모호한 &#39;entity\_id&#39; 열, 쿼리: SELECT \`main\_table\`.\*, \`extension\_attribute\_amazon\_order\_reference\_id* \`. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-15546입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.2.5

**Adobe Commerce 버전과 호환:**

클라우드 인프라의 Adobe Commerce 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

일부 Amazon 확장과 관련된 성능 문제입니다.

<u>필수 구성 요소</u>:

B2B 및 Amazon\_Payment로 Adobe Commerce을 정리합니다.

<u>재현 단계</u>:

1. 상점 첫 페이지로 이동합니다.
1. 장바구니에 제품을 추가합니다.
1. cron 작업 `flush_preview_quotas`을(를) 기다리거나 트리거하십시오.

<u>실제 결과</u>:

`var/log/exception/log`을(를) 확인하면 다음 오류가 표시됩니다.

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table`.*, `확장_attribute_amazon_order_reference_id`.`amazon_order_reference_id` AS `확장_attribute_amazon_order_reference_id_amazon_order_reference_id`, `확장_attribute_amazon_order_reference_id`.`견적_id` AS `확장_attribute_amazon_order_reference_id`, `확장_attribute_amazon_order_reference_id`.` 샌드박스_simulation_reference` AS `확장_attribute_amazon_order_reference_id_sandbox_simulation_reference`, `확장_attribute_amazon_order_reference_id`.`확인` AS `확장_attribute_amazon_order_reference_id_confirmed` FROM `견적` AS `main_table` LEFT JOIN `amazon_quote6_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*` AS `

<u>예상 결과</u>:

Cron 작업이 오류 없이 완료됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
