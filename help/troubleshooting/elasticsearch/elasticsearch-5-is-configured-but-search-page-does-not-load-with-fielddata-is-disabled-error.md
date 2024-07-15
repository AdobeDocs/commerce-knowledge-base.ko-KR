---
title: Elasticsearch 5가 구성되었지만 검색 페이지가 "Fielddata가 비활성화되었습니다..." 오류로 로드되지 않음
description: '이 항목에서는 Elasticsearch 5에서 검색 페이지가 로드되지 않고 다음과 유사한 예외가 throw되는 문제를 해결하는 방법에 대해 설명합니다.'
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Elasticsearch 5가 구성되었지만 검색 페이지가 &quot;Fielddata가 비활성화되었습니다...&quot; 오류로 로드되지 않음

이 항목에서는 검색 페이지가 로드되지 않고 다음과 유사한 예외가 발생하는 Elasticsearch 5의 문제를 해결하는 방법을 설명합니다.

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## 영향을 받는 버전

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>Elasticsearch v.5는 Adobe Commerce 2.3.x에서 더 이상 사용되지 않습니다

## 문제

사전 조건: Elasticsearch 5가 구성되었습니다.

검색 요청 시 다음 예외가 로그에 생성됩니다.

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## 원인

기본적으로 레이어 탐색에는 특정 유형의 제품 속성만 사용할 수 있습니다. 예/아니요, 드롭다운, 다중 선택 및 가격입니다. 따라서 Commerce 관리에서는 다른 유형의 특성을 **계층화된 탐색에서 사용** = *필터링 가능한* 또는 **검색 결과에서 사용** = *예*(으)로 설정할 수 없습니다. 그러나 데이터베이스에서 `is_filterable` 및 `is_filterable_in_search` 값을 직접 변경하여 이 제한을 극복할 수 있는 기술적인 가능성이 있습니다. 이 경우 날짜, 텍스트 등과 같은 다른 속성 유형이 레이어 탐색에서 사용되도록 설정되면 Elasticsearch 5에서 예외가 발생합니다.

이 경우 Dropdown, Multiselect 및 Price 이외의 다른 속성 중 레이어 탐색에서 사용하도록 설정된 속성이 있는지 확인해야 합니다. 다음 쿼리를 실행하여 이러한 속성을 검색합니다.

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

이 검색 결과에는 계층화된 탐색에 사용된 속성 목록이 포함되며, 이 목록에서는 해당 형식을 사용할 수 없습니다. 다음 섹션에 설명된 단계를 수행하여 이 문제를 해결합니다.

## 솔루션

이 문제를 해결하려면 `is_filterable`(즉, 계층 탐색에서 사용됨)과 `filterable_in_search`(즉, 검색 결과 계층 탐색에서 사용됨)을(를) &quot;0&quot;(사용되지 않음)으로 설정해야 합니다. 이렇게 하려면 다음 단계를 수행합니다.

1. 데이터베이스 백업을 만듭니다.
1. [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)과 같은 데이터베이스 도구를 사용하거나 명령줄에서 DB에 수동으로 액세스하여 다음 SQL 쿼리를 실행합니다.

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. 다음 명령을 사용하여 카탈로그 검색 전체 색인 재지정을 실행합니다.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 실행하여 캐시 정리

   ```bash
   bin/magento cache:clean
   ```

또는 **시스템** > **도구** > **캐시 관리**&#x200B;의 Commerce 관리에서 사용할 수 있습니다.

이제 문제 없이 카탈로그 검색을 수행할 수 있습니다.
