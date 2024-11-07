---
title: ElasticSuite 추적 인덱스로 인해 Elasticsearch 문제가 발생합니다.
description: 이 문서에서는 ElasticSuite 플러그인으로 생성된 인덱스 추적으로 인한 Elasticsearch 메모리 문제 문제에 대해 설명합니다.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ElasticSuite 추적 인덱스로 인해 Elasticsearch 문제가 발생합니다.

>[!NOTE]
>
>ElasticSuite 및 관련 애플리케이션은 현재 Adobe에서 지원하지 않는 타사 도구입니다. 이 콘텐츠는 정보 제공용으로만 제공되며 지원 범위에 대해 활성화된 것을 나타내지는 않습니다.

이 문서에서는 ElasticSuite 플러그인으로 생성된 인덱스 추적으로 인한 Elasticsearch 메모리 문제 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

2.8.0 이전 버전의 ElasticSuite에서는 추적 인덱스를 정기적으로 정리할 수 없습니다.

2.9.8 / 2.10.7 이전 버전의 ElasticSuite는 추적 인덱스를 일별 인덱스에 저장하고 있으며, 이로 인해 열린 인덱스의 수가 증가합니다.

## 문제

ElasticSuite 타사 플러그인이 설치된 경우 Elasticsearch 메모리 문제가 발생할 수 있으며, Elasticsearch 서비스가 ElasticSuite 추적 인덱스로 인해 충돌할 수 있습니다. 증상은 다음과 같습니다.

* 메모리 오류 없이 Elasticsearch이 충돌합니다.
* 상태 명령 `curl -m1 localhost:9200/_cluster/health?pretty` 또는 `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`(시작 계정용)을(를) 실행할 때 `unassigned_shards`이(가) 수백 또는 수천 개 있습니다.
* Elasticsearch 또는 사이트 성능이 심각하게 저하됩니다.
* *&quot;Elasticsearch 배포 또는 로그 오류의 클러스터 &quot;*&#x200B;에 활성 노드가 없습니다.
* *&quot;배포 또는 로그 오류에서 [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;*&#x200B;에 대한 매핑 업데이트를 거부합니다.

## 원인

ElasticSuite에는 추적 인덱스를 만드는 새로운 기능이 있습니다. 이러한 추적 지수는 어떤 검색어가 가장 많이 사용되었고, 어떤 검색어가 가장 많은 회전율을 발생시켰으며, 어떤 용어가 결과 없음 페이지로 이어지는지 기록하여 상인이 동의어를 만들어 수정할 수 있습니다. 추적 인덱스는 삭제되지 않으므로 Elasticsearch에 리소스가 부족해지고 충돌합니다.

## 솔루션

### ElasticSuite 버전을 업그레이드하여 추적 인덱스를 정기적으로 정리합니다.

ElasticSuite 플러그인을 2.8.0보다 높은 버전으로 업그레이드한 후에는 인덱스의 정기적인 클리닝을 구성할 수 있습니다.

**스토어** > **구성** > **추적** > **전역 구성** > **유지 지연**(으)로 이동

기본 보존 기간은 365일입니다. 30일 또는 15일로 줄일 수 있습니다

### 일별 기반 색인 대신 월별 기반 색인을 사용하도록 ElasticSuite 버전을 업그레이드하십시오

ElasticSuite 플러그인을 버전 > 2.9.8 / 2.10.7로 업그레이드하면 추적 인덱스가 월별 기준으로 설정됩니다.

보존 기간 을 줄일 수 있습니다.

**스토어** > **구성** > **추적** > **전역 구성** > **유지 지연**(으)로 이동

기본 보존 기간은 12개월입니다(12개의 인덱스를 생성). 3개월 또는 6개월로 줄일 수 있습니다.

### cronjob을 사용하여 추적 인덱스 데이터 정리

추적 인덱스를 삭제하는 크론 작업을 만듭니다. 이 명령은 지난 달에 생성된 인덱스를 삭제합니다.

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

설정된 시간 빈도에서 인덱스를 삭제하려면 개발자 설명서에서 다음 문서를 참조하여 cron 작업을 만듭니다.

* [사용자 지정 cron 작업 및 cron 그룹 구성(튜토리얼)](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/crons/custom-cron-tutorial)
* [cron 작업 설정](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property)
