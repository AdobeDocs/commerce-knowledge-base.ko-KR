---
title: 색인이 무효화되고 'indexer_reindex_all_invalid'가 계속 실행됩니다.
description: 색인이 무효화되고 'indexer_reindex_all_invalid'가 계속 실행됩니다.
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# 인덱스가 무효화되고 `indexer_reindex_all_invalid`이(가) 계속 실행됩니다.

이 문서에서는 지속적인 리인덱싱으로 인해 사이트에 성능 문제가 발생하는 경우 이 문제에 대해 가능한 해결 방법을 제공합니다. 이 문제는 [!DNL cron] 작업 `indexer_reindex_all_invalid`이(가) 계속 실행되고 [!DNL reindex]에 캐시가 정리되었기 때문에 발생합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(cloud &amp; on-premise) 2.4.0+(**[!UICONTROL Category Permissions]**&#x200B;은(는) Adobe Commerce 전용 기능이므로 Magento Open Source에 영향을 주지 않습니다.)

## 문제

[!DNL New Relic One]에서 오류 로그는 1초 이상의 시간 동안 `indexer_update_all_views`이(가) 여러 번 실행되는 것을 표시해야 합니다(즉, 처리 중).

## 원인

핵심 Adobe Commerce 임포터가 수동으로 또는 [!DNL cron]에 의해 실행되면 여러 핵심 모듈에 대한 플러그인 집합이 실행되어 무효화해야 할 인덱스를 결정합니다.

[!DNL Commerce Admin]에서 **[!UICONTROL Category Permissions]** 모듈을 사용하도록 설정하면 문제가 발생합니다. true인 경우 모듈의 플러그인은 가져오기가 실행될 때 항상 제품 및 카테고리 색인(및 연결된 색인)을 무효화합니다. 표준 가져오기 형식을 검사하면 모두 **[!UICONTROL Category Permissions]**&#x200B;에 영향을 줍니다. 무효화가 예상됩니다.

또한 사이트에 B2B 모듈이 활성화되어 있으면 **[!UICONTROL Shared Catalog]**&#x200B;이(가) 활성화되어 있으면 켜지고 **[!UICONTROL Category Permissions]**&#x200B;을(를) 잠급니다. **[!UICONTROL Shared Catalog]**&#x200B;을(를) 끄면 **[!UICONTROL Category Permissions]**&#x200B;의 잠금을 해제하지만 끄지 않습니다.

<u>[!DNL MySQL] 데이터베이스에서 [!DNL cron] 로그 확인</u>:

[!DNL MySQL] 데이터베이스에 로그인하면 `cron` 로그에서 **[!DNL reindex all indexes]** 프로세스를 확인할 수 있습니다.
이 **은(는) 여러 번 나타나야 하지만** 프로세스는 가능한 두 가지 중 하나를 수행한다는 것이 중요합니다.

프로세스는 다음 두 가지 중 하나만 수행할 수 있습니다.

1. Nothing: 0초에서 1초(1초 이하) 정도 소요됩니다. 프로세스는 수행해야 할 작업이 있는지 확인한 후, 필요하지 않은 경우 중지합니다.
1. [!DNL Reindex]개 모두: 항상 시간(보통 분)이 소요됩니다.

일반적으로 실행 시간이 1초 미만인 상태에서 많은 프로세스가 발생하는 것을 보고자 합니다.
따라서 판매자는 이 [!DNL MySQL] 쿼리를 사용하여 **1초 이상**&#x200B;이 소요되는 트랜잭션을 찾을 수 있습니다.

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

다음을 실행하여 기간이 얼마나 오래 기록되는지 볼 수 있습니다.

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

적절한 평가를 수행하기에 충분한 기간이 없다면 이 [[!DNL Cron] (예약된 작업)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 가이드를 따라 성공적인 `cron` 프로세스가 로그에 유지되는 시간을 늘리고 **[!DNL Success History Lifetime]** 값을 늘릴 수 있습니다(기본값은 60분).


## 솔루션

`afterImportSource` 메서드가 사용자 지정 가져오기를 제외하도록 `Magento\CatalogPermissions\Model\Indexer\Plugin\Import`을(를) 확장합니다.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

여기서 `ENTITY_CODE`은(는) 사용자 지정 가져오기의 `import.xml` 파일에서 엔터티 이름 매개 변수에 사용된 값입니다.

## 관련 읽기

Adobe Commerce 작업 구성 안내서의 [구성 [!DNL cron] 작업](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html).
