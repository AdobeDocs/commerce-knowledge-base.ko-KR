---
title: Adobe Commerce 문제 해결사의 Elasticsearch
description: Adobe Commerce의 Elasticsearch 문제는 Elasticsearch 문제 해결사 도구를 사용하여 해결할 수 있습니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Adobe Commerce 문제 해결사의 Elasticsearch

Adobe Commerce의 Elasticsearch 문제는 Elasticsearch 문제 해결사 도구를 사용하여 해결할 수 있습니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.

>[!WARNING]
>
>Adobe Commerce on cloud infrastructure의 경우 48시간 동안 인프라 팀에 통지하지 않으면 서비스 업그레이드를 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 사항이 프로덕션에 적용되기 48시간 전에 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 필요한 서비스 업그레이드에 대해 자세히 설명하고 업그레이드 프로세스를 시작할 시간을 지정하십시오.

## 1단계 - Elasticsearch 문제 확인 {#step-1}

+++**Elasticsearch과 관련된 문제를 해결할 수 있습니까?**

오류 메시지, &quot;_클러스터에 활성 노드가 없음&quot;,_&#x200B;제품 누락 및 이전 제품 정보 표시로 표시되는 Elasticsearch 문제.

a. 예 - [2단계](#step-2)로 진행합니다.\
b. 아니요 - [Adobe Commerce 도움말 센터 기술 자료](https://support.magento.com/hc)에서 관련 검색어를 다시 검색합니다.

+++

## 2단계 - 설치 문제 확인 {#step-2}

+++**Elasticsearch을 새로 설치했습니까?**

a. 예 - [Elasticsearch이 제대로 설치되었는지 확인하십시오.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) 또한 클라우드 인프라 2.3.1 이상에서 Adobe Commerce에 있는지 확인합니다. 클라우드 인프라(버전 2.3.1 이상)에서 Adobe Commerce으로 업그레이드하고 6.x 이전 버전의 Elasticsearch에 있는 판매자는 배포 시 오류가 발생할 수 있습니다. 이 문제를 해결하려면 Elasticsearch 클라이언트 모듈과 Elasticsearch 서비스가 권장 최신 버전이어야 합니다. 단계는 [클라우드 인프라 2.3.1 이상에서 Adobe Commerce 이후 Elasticsearch 문제](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md)를 참조하십시오.\
b. 아니요 - 클러스터의 상태를 확인합니다. Pro 스테이징 또는 프로덕션 환경에 있는 경우 `curl -m1 localhost:9200/_cluster/health?pretty` 명령을 실행합니다. 모든 스타터 분기를 포함하는 통합 환경에 있는 경우 `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`을(를) 실행합니다. [3단계](#step-3)로 진행합니다.

+++

## 3단계 - Elasticsearch 클러스터를 사용할 수 있는지 확인 {#step-3}

+++**서비스 응답을 받았습니까?**

a. 예 - [4단계](#step-4)로 진행합니다.\
b. 아니요 - [9](#step-9)단계로 진행합니다.

+++

## 4단계 - Elasticsearch 클러스터 정상 확인 {#step-4}

+++**녹색 응답**

a. 예 - Elasticsearch을 데이터 처리에 사용할 수 있으며 리인덱싱이 작동해야 합니다. [5단계](#step-5)로 진행합니다.\
b. 아니요 - 노란색 또는 빨간색은 노드 간 연결에 문제가 있음을 의미하며 일부 데이터를 사용할 수 없을 수도 있습니다. 노란색이면 `php bin/magento config:show catalog/search/engine` 명령을 실행하여 검색 엔진을 확인합니다. [6단계](#step-6)로 진행합니다. 빨간색이면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하세요.

+++

## 5단계 - 검색 작동 확인 {#step-5}

+++**검색 문제**

증상에는 제품 없음, 빈 범주 또는 제품 또는 제품 범주가 올바르지 않은 업데이트가 없을 수 있습니다.

a. 예 - 이 명령을 실행하여 카탈로그 검색 상태를 확인합니다. `php bin/magento indexer:status`. [8단계](#step-8)로 진행합니다.\
b. 아니요 - 명령 실행: `php bin/magento config:show catalog/search/engine`. [6단계](#step-6)로 진행합니다.

+++

## 6단계 - ElasticSuite 확인 {#step-6}

+++**ElasticSuite를 사용 중입니까?**

a. 예 - 다음 명령을 실행하여 ElasticSuite가 현재 버전인지 확인하십시오. `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` 이 버전이 더 이상 사용되지 않거나 권장되는지 확인하려면 [Github: Smile-SA/elasticsuite](https://github.com/Smile-SA/elasticsuite)를 참조하십시오. ElasticSuite가 최신 상태이면 [10단계](#step-10)로 진행합니다.\
b. 아니요 - [7단계](#step-7)로 진행합니다.

+++

## 7단계 - ECE-tools 최신 확인 {#step-7}

+++**ECE-tools가 최신 버전입니까?**

`php ./vendor/bin/ece-tools -V` 명령을 실행하고 ECE-tools 버전을 확인합니다. [최신 버전의 ECE-tools](https://github.com/magento/ece-tools/releases)입니까?

a. 예 - [5a단계](#step-5)로 진행합니다.\
b. 아니요 - ECE-tools 를 최신 버전으로 업그레이드합니다. `php bin/magento config: show catalog/search/engine` 명령을 실행하여 검색 엔진을 확인합니다. [6단계](#step-6)로 진행합니다.

+++

## 8단계 - 리인덱싱 확인 {#step-8}

+++**카탈로그 검색 상태가 _처리 중_입니까?**

a. 예 - 처리가 완료될 때까지 기다린 후 제품 범주가 업데이트되었는지 확인해야 합니다. 아직 제출하지 않은 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.\
b. 아니요 - 카탈로그 검색 상태가 _색인 재지정 필요_&#x200B;인 경우 CLI/터미널: `php bin/magento cron:run`에서 실행합니다. 작동하지 않으면 `php bin/magento indexer:reindex`을(를) 실행하십시오. 그래도 문제가 해결되지 않으면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

+++

## 9단계 - yaml 구성 확인 {#step-9}

+++**`.yaml`파일이 최근에 업데이트되었습니까?**

a. 예 - DevDocs [Elasticsearch 설정: Elasticsearch을 사용하려면](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)을(를) 참조하여 `.yaml` Elasticsearch 구성을 확인합니다.\
b. 아니요 - [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 10단계 - 추적 인덱스 확인 {#step-10}

+++**나열된 추적 인덱스가 있습니까?**

모든 시작 분기를 포함하는 통합 환경에 있는 경우 `curl elasticsearch.internal:9200/_cat/indices`을(를) 실행합니다. Pro 스테이징 또는 프로덕션 환경에 있는 경우 `curl localhost:9200/_cat/indices`을(를) 실행합니다. 추적 인덱스가 나열됩니까? `_tracking_log_`에 대한 출력을 확인합니다.

a. 예 - ElasticSuite 버전 2.8.0 이전 버전인 경우 [ElasticSuite 2.8.0으로 업그레이드하여 추적 인덱스를 조정하거나 추적을 비활성화하는 것이 좋습니다](https://support.magento.com/hc/en-us/articles/360035266131?). 즉시 업그레이드할 수 없는 경우 [크론을 만들어 추적 인덱스를 제거할 수 있습니다](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). 그러나 이로 인해 성능 문제가 발생할 수 있습니다. ElasticSuite 2.8.0으로 업그레이드하거나 추적 인덱스를 제거하면 명령을 실행합니다(Pro 스테이징 또는 프로덕션 환경에 있는 경우).`localhost:9200/_cat/allocation?v` 사용 가능한 공간을 확인합니다. 모든 시작 분기를 포함하는 통합 환경 중 하나에 있는 경우 `elasticsearch.internal:9200/_cat/allocation?v`을(를) 실행합니다. [11단계](#step-11)로 진행합니다.\
b. 아니요 - Pro 스테이징 또는 프로덕션 환경에 있는 경우 `localhost:9200/_cat/allocation?v`을(를) 실행하고 사용 가능한 공간을 확인합니다. 모든 시작 분기를 포함하는 통합 환경 중 하나에 있는 경우 `elasticsearch.internal:9200/_cat/allocation?v`을(를) 실행합니다. [11단계](#step-11)로 진행합니다.

+++

## 11단계 - 특정 오류 조회 {#step-11}

+++**특정 오류**

Adobe Commerce 및 ES 로그, 확장 및 사용자 지정 코드.

a. 예 - Adobe Commerce 도움말 센터 문제 해결 문서 [Elasticsearch이 제대로 설치되었는지 확인](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) 또는 [ElasticSuite 플러그인을 사용할 때 Elasticsearch 충돌 또는 메모리 부족 문제가 있는지 확인](https://support.magento.com/hc/en-us/articles/360035266131)을 검토하십시오.\
b. 아니요 - [12단계](#step-12)로 진행합니다.

+++

## 12단계 - 사용 가능한 스토리지 확인 {#step-12}

+++**저장소 사용량 > 85%**

a. 예 - 사용 가능한 스토리지를 늘려야 합니다. DevDocs[Elasticsearch 설정: Elasticsearch을 활성화하려면](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)을(를) 참조하십시오. 그런 다음 `localhost:9200/_cat/allocation?v`을(를) 실행합니다(Pro 스테이징 또는 프로덕션 환경에 있는 경우). 모든 스타터 분기를 포함하는 통합 환경 중 하나에 있는 경우 `elasticsearch.internal:9200/_cat/allocation?v`을(를) 실행합니다. [11단계](#step-11)로 진행합니다.\
b. 아니요 - [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[1단계로 돌아가기](#step-1)
