---
title: 색인이 다른 프로세스에 의해 잠겼습니다.
description: 이 문서에서는 색인이 다른 프로세스에 의해 잠기고 건너뛴 Adobe Commerce의 일반적인 색인화 문제에 대해 설명합니다.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 색인이 다른 프로세스에 의해 잠겼습니다.

이 문서에서는 색인이 다른 프로세스에 의해 잠기고 건너뛴 Adobe Commerce의 일반적인 색인화 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.X

## 문제

CLI에서 전체 색인 재지정 중에 Adobe Commerce에 다음과 같은 오류 메시지가 표시됩니다. *색인이 다른 색인 재지정 프로세스에 의해 잠겼습니다. 건너뛰기.&#39;* 다시 말해, 프로세스나 색인 유형이 잠겨 있으면 그 특정 색인 유형을 다시 색인화할 수 없습니다. 색인 재지정은 항상 해당 색인 유형을 건너뜁니다.

## 원인

이전 색인이 성공적으로 완료되지 않은 경우 이 오류가 발생할 수 있습니다. 몇 가지 가능한 이유는 다음과 같습니다.

* 다른 프로세스 또는 사용자에 의해 프로세스가 중단되었습니다.
* 메모리 제한.
* 시간 초과와 같은 MySQL 오류.
* 다시 색인화하는 동안 치명적인 PHP 오류가 발생했습니다.

## 재현 단계

1. 예를 들어    ```bash    cataloginventory_stock ```    색인 유형이 잠겨 있습니다.
1. CLI 명령을 실행하여 모든 데이터를 다시 인덱싱하려고 할 때    ```bash    php bin/magento indexer:reindex    ```, 다음 출력 결과를 가져옵니다.    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. 위에서 볼 수 있듯이    ```bash    cataloginventory_stock```    인덱스 프로세스를 건너뛰었습니다.


## 솔루션

색인 상태를 재설정한 다음 새 색인 재지정 프로세스를 실행해야 합니다. 인덱스 재설정 상태의 경우 다음 명령을 실행해야 합니다.

```bash
bin/magento indexer:reset <index identifier>
```

인덱스 식별자(코드)가 무엇인지 확실하지 않은 경우 다음 명령을 사용하여 나열할 수 있습니다.

```bash
bin/magento indexer:info
```

완성도를 위해 기본 인덱스에 대해 가능한 모든 조합은 다음과 같습니다.

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## 관련 읽기

지원 기술 자료에서:

* [Cron 작업은 다른 그룹의 작업을 잠급니다(클라우드 인프라의 Adobe Commerce).](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

사용 안내서에서 다음을 수행합니다.

* [색인 관리](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/tools/index-management?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

개발자 설명서에서:

* [인덱싱 개요](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [인덱서 모범 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/performance-best-practices/configuration)
* [Cron 구성 및 실행](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [인덱서 관리](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/cli/manage-indexers)
* [인덱서 최적화](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
