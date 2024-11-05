---
title: 데이터베이스에 동일한 엔터티의 행이 여러 개 있습니다.
description: 이 문서에서는 데이터베이스에 동일한 엔티티 ID에 대한 행이 여러 개 있는 문제에 대한 해결 방법을 제공합니다.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# 동일한 엔터티에 대한 데이터베이스의 여러 행

이 문서에서는 데이터베이스에 동일한 엔티티 ID에 대한 행이 여러 개 있는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전:

* Adobe Commerce(모든 버전)

## 문제

데이터베이스에 동일한 엔티티 ID에 대한 행이 여러 개 있습니다.

예를 들어, 이 쿼리를 실행할 때 중복 엔티티 ID가 있는 레코드 목록을 수신한 후 다음을 수행합니다.

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

범주/제품/장바구니 가격 규칙/카탈로그 가격 규칙/CMS 페이지의 `$entityID = ID`입니다.

| 엔티티 | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| 범주/제품 | catalog_category_entity/catalog_product_entity | entity_id |
| 장바구니 가격 규칙/카탈로그 가격 규칙 | salesrule/catalogrule | rule_id |
| CMS 페이지 | cms_page | page_id |

## 원인

이는 예상되는 비헤이비어입니다. 여러 행은 콘텐츠 스테이징 기능에 의해 만들어집니다.

* 종료 날짜 없이 시작 날짜를 지정하면 엔티티/규칙/페이지 ID가 동일한 행이 두 개 이상 있습니다. 한 행은 엔터티의 원래 상태(`created_in=1`이 있는 행)를 나타내고, 한 행은 *예약된 업데이트의 끝*&#x200B;을 나타냅니다.

* 종료 날짜가 포함된 시작 날짜를 지정하는 경우 동일한 엔티티/규칙/페이지 ID를 가진 행이 최소 3개 있습니다. 한 행은 엔티티의 원래 상태(`created_in=1`이 있는 행)를 나타내고, 한 행은 *예약된 업데이트의 시작*&#x200B;에 해당하며, 한 행은 *예약된 업데이트의 종료*&#x200B;에 해당합니다.

예를 들어 이 쿼리에서 다음을 수행합니다.

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* `created_in` 및 `updated_in` 값은 다음 패턴을 따라야 합니다. 현재 행의 `created_in` 값은 이전 행의 `updated_in` 값과 같습니다. 또한 첫 번째 행에는 `created_in = 1`이(가) 포함되어야 하며 마지막 행에는 `updated_in = 2147483647`이(가) 있어야 합니다. 행이 하나만 있으면 `created_in=1` 및 `updated_in=2147483647`이(가) 표시됩니다.

### 두 번째 DB 항목(및 다음 항목 모두)이 동일한 엔티티의 DB에 표시되는 이유는 무엇입니까?

* 영향을 받는 엔터티에 대한 두 번째 DB 레코드(및 가능한 다음 레코드)는 `Magento_Staging` 모듈을 사용하여 콘텐츠 스테이징 업데이트가 예약되었음을 의미합니다. 이는 각 테이블의 엔터티에 대해 추가 레코드를 만듭니다.

`created_in` 또는 `updated_in` 열에 대해 레코드에 동일한 값이 있는 경우에만 문제가 발생합니다.

## 솔루션

이는 예상되는 동작이며 행 간에 불일치가 있는 경우에만 문제가 발생합니다.

## 관련 읽기

* 지원 기술 자료에서 [범주의 변경 내용이 저장되지 않음](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html)
* 지원 기술 자료에서 [일정 업데이트의 종료 날짜를 편집한 후 카탈로그 테이블에 있는 항목이 중복됨](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
