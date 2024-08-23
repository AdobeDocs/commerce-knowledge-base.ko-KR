---
title: ' [!DNL Commerce Data Exporter] 피드 및 [!DNL cron] 로그 테이블에서 업데이트되지 않은 데이터 수정 오류가 존재하지 않습니다.'
description: 이 문서에서는  [!DNL Commerce Data Exporter mview] 구독에서 잘못된 보기 ID를 사용하여 발생한 데이터 동기화 문제를 해결하는 솔루션을 제공합니다.
feature: Data Import/Export, Saas, Logs
role: Developer
source-git-commit: cf87b5f1280a2d1d23c7ace37616feb337b5142f
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Commerce Data Exporter] 피드에서 데이터가 업데이트되지 않고 변경 로그 테이블의 [!DNL cron] 로그 오류가 존재하지 않습니다.

이 문서에서는 [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) 구독에서 잘못된 보기 ID를 사용하여 발생한 데이터 동기화 문제를 해결하는 솔루션을 제공합니다. [!DNL Mview] 구독은 데이터베이스 테이블에 대한 변경 내용을 추적하는 데 사용됩니다.

## 영향을 받는 제품 및 버전

사용자 지정 코드가 데이터 내보내기 기능(`commerce-data-exporter` 또는 `saas-exporter`)에 적용된 Adobe Commerce 인스턴스. 설치된 [[!DNL SaaS] 데이터 내보내기 버전이 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) 이상이고 코드가 `catalog_data_exporter_products` 인덱스를 직접 참조하는 경우 오류가 발생합니다.

## 문제

판매자는 카탈로그 [!DNL Data Exporter] 피드 테이블에서 데이터 업데이트가 누락되었음을 확인하고 [!DNL cron] 작업 로그에서 다음 오류를 확인할 수 있습니다.

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## 원인

[!DNL Commerce Data Export] [버전 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9) 릴리스의 피드 테이블, 인덱스 및 변경 로그 테이블의 이름 변경으로 인해 [!DNL Commerce Data Export] 확장을 사용하는 사용자 지정 확장의 [!DNL Mview] 구독이 제대로 작동하지 않을 수 있습니다.

이 경우 `catalog_data_exporter` 테이블 이름이 `cde_products_feed`(으)로 변경되었으며 [!DNL Data Exporter Mview] 구독에서 이전 이름을 참조하는 사용자 지정 코드가 있으므로 *테이블이 없습니다* 오류가 발생합니다.

## 솔루션

사용자 지정된 확장에서 [!DNL Mview] 구성 파일(```./etc/mview.xml```)을 편집하여 `catalog_data_exporter_products` 테이블 이름을 *`cde_products_feed`*(으)로 변경합니다.

다음 예제에서는 [!DNL Mview] 구독에서 추적한 테이블을 지정하는 코드를 보여 줍니다.

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## 관련 읽기

[!DNL SaaS] 서비스에 대한 Adobe Commerce 데이터 내보내기 안내서의 [[!DNL SaaS] 데이터 내보내기 확장 릴리스 노트](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes).
