---
title: 라이브 검색 카탈로그가 동기화되지 않음
description: 이 문서에서는 라이브 검색 확장을 사용할 때 카탈로그 데이터가 올바르게 동기화되지 않는 Adobe Commerce 문제에 대한 해결 방법을 제공합니다.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 5911b436fdcc08e695fb14d35784287945593815
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# 라이브 검색 카탈로그가 동기화되지 않음

이 문서에서는 라이브 검색 확장을 사용할 때 카탈로그 데이터가 올바르게 동기화되지 않는 Adobe Commerce 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 라이브 검색 확장이 설치된 Adobe Commerce 2.4.x

## 문제

카탈로그 데이터가 올바르게 동기화되지 않았거나 새 제품이 추가되었지만 검색 결과에 표시되지 않습니다. `var/log/exception.log`에서 다음 오류가 발생할 수도 있습니다.

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>테이블 이름 `catalog_data_exporter_products` 및 `catalog_data_exporter_product_attributes`은(는) 이제 [!DNL Live Search] 버전 4.2.1부터 `cde_products_feed` 및 `cde_product_attributes_feed`(으)로 호출됩니다. 4.2.1 이전 버전의 판매자의 경우 이전 테이블 이름 `catalog_data_exporter_products` 및 `catalog_data_exporter_product_attributes`에서 데이터를 찾습니다.

<u>재현 단계</u>

1. 사용자 설명서의 [라이브 검색 설치 > API 키 구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=ko#configure-api-keys)에 설명된 대로 Adobe Commerce 인스턴스에 대한 라이브 검색을 구성하고 연결합니다.
1. 30분 후 사용자 설명서의 [라이브 검색 설치 > 내보내기 확인](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=ko#verify-export)에 설명된 대로 내보낸 카탈로그 데이터를 확인합니다.
1. 30분 후 사용자 설명서의 [라이브 검색 설치 > 연결 테스트](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=ko#test-connection)에 설명된 대로 연결을 테스트하십시오.

Or

1. 카탈로그에 새 제품을 추가합니다.
1. Magento indexer + cron 이 데이터를 백엔드 서비스에 동기화하기 위해 실행한 시간으로부터 15~20분 후 제품 이름 또는 기타 검색 가능한 속성을 사용하여 검색 쿼리를 실행해 보십시오.

<u>예상 결과</u>

* 내보낸 카탈로그 데이터를 확인할 수 있습니다.
* 연결 성공
* 검색 결과에 새 제품이 표시됩니다.

<u>실제 결과</u>

API 키가 변경되어 내보낸 카탈로그를 확인할 수 없거나 연결이 설정되지 않았습니다.

## 솔루션

카탈로그 동기화 문제를 해결하기 위해 시도할 수 있는 몇 가지 방법이 있습니다.

### 변경 사항이 적용될 때까지 대기

구성하고 연결되면 ES(Elasticsearch)의 색인이 만들어지고 검색 결과가 반환되는 데 30분 이상 걸릴 수 있습니다. 이후 일회성 제품 업데이트가 몇 분 안에 색인화될 것으로 예상됩니다.

### 특정 SKU에 대한 제품 데이터 동기화

제품 데이터가 특정 SKU에 대해 올바르게 동기화되지 않는 경우 다음을 수행합니다.

1. 다음 [!DNL SQL] 쿼리를 사용하여 `feed_data` 열에 예상한 데이터가 있는지 확인하십시오. `modified_at` 타임스탬프도 메모해 두십시오.

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   For example:

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. 올바른 데이터가 표시되지 않으면 다음 명령을 사용하여 다시 인덱싱하고 1단계에서 [!DNL SQL] 쿼리를 다시 실행하여 데이터를 확인하십시오.

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. 그래도 올바른 데이터가 표시되지 않으면 [지원 티켓을 만듭니다](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### 마지막 제품 내보내기의 타임스탬프 확인

1. `cde_products_feed`에 올바른 데이터가 표시되면 다음 [!DNL SQL] 쿼리를 사용하여 마지막 내보내기의 타임스탬프를 확인하십시오. `modified_at` 타임스탬프 이후여야 합니다.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. 타임스탬프가 오래된 경우 다음 cron 실행이 완료될 때까지 기다리거나 다음 명령을 사용하여 직접 트리거할 수 있습니다.

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. `<>`시간 동안(증분 업데이트 시간) 기다립니다. 데이터가 여전히 표시되지 않으면 [지원 티켓을 만드세요](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### 특정 속성 코드 동기화

제품 속성 데이터가 특정 속성 코드에 대해 올바르게 동기화되지 않는 경우 다음을 수행합니다.

1. 다음 [!DNL SQL] 쿼리를 사용하여 `feed_data` 열에 예상한 데이터가 있는지 확인하십시오. `modified_at` 타임스탬프도 메모해 두십시오.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. 올바른 데이터가 표시되지 않으면 다음 명령을 사용하여 인덱스를 다시 만든 다음 1단계에서 [!DNL SQL] 쿼리를 다시 실행하여 데이터를 확인합니다.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. 그래도 올바른 데이터가 표시되지 않으면 [지원 티켓을 만듭니다](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### 마지막 제품 속성 내보내기의 타임스탬프 확인

`cde_product_attributes_feed`에 올바른 데이터가 표시되면:

1. 마지막 내보내기의 타임스탬프를 확인하려면 다음 [!DNL SQL] 쿼리를 사용하세요. `modified_at` 타임스탬프 이후여야 합니다.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. 타임스탬프가 오래된 경우 다음 cron 실행이 완료될 때까지 기다리거나 다음 명령을 사용하여 직접 트리거할 수 있습니다.

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 15~20분 동안(증분 업데이트 시간) 기다립니다. 데이터가 여전히 표시되지 않으면 [지원 티켓을 만드십시오](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### API 구성 변경 후 동기화

(알려진 문제) API 구성을 변경하여 데이터 공간 ID가 변경되고 카탈로그 변경 사항이 더 이상 동기화되지 않는 경우 다음 명령을 실행하여 피드를 다시 동기화합니다.

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

Live Search 색인의 다시 색인을 요청하려면 [지원 요청을 제출](https://experienceleague.adobe.com/home?lang=ko&support-tab=home#support)하세요. 문제 설명에서 **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]** 아래의 관리 패널에 있는 데이터 공간/환경 ID를 포함합니다.

>[!IMPORTANT]
>다른 경우에 `--cleanup-feed` 옵션을 사용하면 데이터 손실 및 데이터 동기화 문제가 발생할 수 있습니다.  새 빈 환경이 있거나, Adobe 팀이 데이터 공간 정리 작업을 완료한 후 또는 [—dry-run](https://experienceleague.adobe.com/ko/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run) 옵션을 사용하여 `saas:resync` 명령을 실행하는 경우에만 사용합니다. 다른 경우에 `--cleanup-feed` 옵션을 사용하면 데이터 손실 및 데이터 동기화 문제가 발생할 수 있습니다.

## 관련 읽기

* 사용자 설명서의 [실시간 검색 온보딩](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html?lang=ko)
* Adobe Commerce SaaS 데이터 내보내기 안내서의 [로그 검토 및 Adobe Commerce SaaS 데이터 내보내기 및 동기화 문제 해결](https://experienceleague.adobe.com/ko/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
