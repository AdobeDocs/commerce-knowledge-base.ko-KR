---
title: 일정 업데이트의 종료 날짜를 편집한 후 카탈로그 테이블의 항목이 중복됨
description: 이 문서에서는 카탈로그 가격 규칙 일정 업데이트의 종료 날짜 또는 시간을 편집하여 "catalogle" 테이블에 중복 항목을 추가하고 "catalogle_rule"(카탈로그 규칙 제품) 인덱서 리인덱스에서 오류가 발생하는 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다.
exl-id: e900b712-d0f5-4404-8441-64522035ce44
feature: Cache, Catalog Management, Marketing Tools
role: Developer
source-git-commit: 496151d1fe29a66d84349e4a96e7c5563a92c5c4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 일정 업데이트의 종료 날짜를 편집한 후 카탈로그 테이블의 항목이 중복됨

이 문서에서는 카탈로그 가격 규칙 일정 업데이트의 종료 날짜 또는 시간을 편집하여 `catalogrule` 테이블에 중복 항목을 추가하고 `catalogrule_rule`(카탈로그 규칙 제품) 인덱서 다시 인덱스에서 오류가 발생하는 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다.

## 문제

기존 카탈로그 가격 규칙 일정 업데이트의 종료 날짜 또는 시간을 변경하면 `catalogrule` 데이터베이스 테이블에 중복 항목이 만들어집니다. 따라서 예외 로그에 다음 오류가 발생하여 `catalogrule_rule` 다시 인덱싱이 실패합니다. *같은 ID를 가진 항목이 이미 있습니다*.

<u>재현 단계</u>:

필수 구성 요소: `catalogrule_rule` 인덱서가 *[일정에 따라 업데이트](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)* 모드로 설정되어 있습니다.

1. Commerce 관리자의 **마케팅** > **프로모션** > **카탈로그 가격 규칙**&#x200B;에서 새 카탈로그 가격 규칙을 만듭니다.
1. **카탈로그 가격 규칙** 그리드에서 **편집**&#x200B;을 클릭하고 새 업데이트를 예약한 다음 **상태**&#x200B;를 *활성*(으)로 설정합니다.
1. 새로 만든 업데이트 옆의 **보기/편집**&#x200B;을 클릭하고 종료 날짜를 이전 시간으로 변경합니다.
1. 업데이트를 저장합니다.
1. `catalogrule_rule` 인덱서에 대해 reindex 명령을 실행합니다.

<u>예상 결과</u>:

`catalogrule_rule` 인덱서가 다시 인덱싱되었습니다. `catalogrule` 테이블에 중복된 항목이 없습니다.

<u>실제 결과</u>:

`catalogrule` 테이블에 중복 항목이 있으므로 다시 인덱싱이 실패하고 다음 오류가 발생했습니다. *ID가 같은 항목이 이미 있습니다*.

## 솔루션

이 문제를 해결하려면 첨부된 패치를 적용하고 기존 중복 항목을 제거해야 합니다. 중복 항목이 있는지 확인하고 제거하는 방법에 대한 자세한 내용은 [중복된 항목 제거](#remove) 섹션을 참조하십시오.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-10974\_EE\_2.2.3\_COMPOSER\_v2.patch 다운로드](assets/MDVA-10974_EE_2.2.3_COMPOSER_v2.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 2.2.3

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라의 Adobe Commerce 2.2.1 - 2.2.5
* Adobe Commerce 온-프레미스 2.2.1 - 2.2.2 및 2.2.4 - 2.2.5

## 패치 적용 방법

지원 기술 자료의 지침은 [Adobe에서 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 중복된 항목 제거 {#remove}

>[!NOTE]
>
>조작하기 전에 최근 백업이 있는지 확인하십시오.

다음 단계를 수행하여 복제된 항목을 찾아 삭제합니다.

1. 다음 쿼리를 실행하여 중복 항목이 데이터베이스에 있는지 확인합니다.

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   중복 항목이 없으면 응답은 비어 있으므로 다른 작업을 수행하지 않아도 됩니다. 중복된 항목이 있으면 다음 예제와 같이 테이블 이름과 중복된 엔터티의 `entity_id`이(가) 표시됩니다.

   ![table_results1.png](assets/table_results1.png)

   특정 테이블에서 엔터티 ID가 있는 필드의 이름이 `entity_id`과(와) 다르다는 점을 고려하십시오. 예를 들어 `cms_page` 테이블에서 `entity_id` 대신 `page_id`이(가) 됩니다.

1. 그런 다음 중복 항목을 자세히 살펴보고 제거해야 하는 사항을 이해해야 합니다. 중복을 확인하려면 다음과 유사한 쿼리를 사용하십시오. 이전 단계에서 받은 결과에 따라 테이블 이름, 엔티티 ID 이름 및 값을 바꿉니다.

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   여러 열이 있는 레코드 목록을 받게 됩니다. 예:

   ![table_results2.png](assets/table_results2.png)

   `created_in` 및 `updated_in` 값은 다음 패턴을 따라야 합니다. 현재 행의 `created_in` 값은 이전 행의 `updated_in` 값과 같습니다. 또한 **첫 번째 행**&#x200B;은(는) created\_in = 1을 포함해야 하며 **마지막 행**&#x200B;은(는) updated\_in = 2147483647을 포함해야 합니다. (행이 한 개만 있는 경우 created\_in=1 **및** updated\_in=2147483647이 표시되어야 합니다.) 이 패턴이 깨진 행을 삭제해야 합니다. 이 예제에서는 두 번째와 세 번째 행이 모두 created_in: 1540837826에 대해 동일한 값을 공유하므로 `row_id` =2052가 있는 행이 됩니다.

1. 다음과 유사한 쿼리를 사용하여 중복을 삭제합니다. 이전 단계에서 받은 결과에 따라 테이블 이름, 엔티티 ID 이름 및 값을 바꿉니다.

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. 다음을 실행하여 캐시 정리:

   ```bash
   bin/magento cache:clean
   ```

   또는 **시스템** > **도구** > **캐시 관리**&#x200B;의 Commerce 관리에서 사용할 수 있습니다.

## 개발자 설명서에 있는 유용한 링크

* [클라우드 인프라의 Adobe Commerce에 사용자 지정 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [클라우드 인프라에서 Adobe Commerce에 대한 로그 보기 및 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## 첨부 파일
