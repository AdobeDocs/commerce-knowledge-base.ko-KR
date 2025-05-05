---
title: Elasticsearch 색인 상태가 '노란색' 또는 '빨간색'입니다.
description: 이 문서에서는 Elasticsearch 인덱스 상태가 '*green*'이 아닌 경우에 대한 수정 사항을 제공합니다. '*노란색*'은 일반을 나타내고 '*빨간색*'은 잘못된 것을 나타냅니다. '노란색' 또는 '빨간색' 상태는 제품 누락 또는 이전 제품 정보 표시와 함께 발생할 수 있습니다.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Elasticsearch 색인 상태가 &#39;노란색&#39; 또는 &#39;빨간색&#39;입니다.

>[!WARNING]
>
> [MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거됩니다](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). 버전 2.4.0을 설치하기 전에 Elasticsearch 호스트를 설정하고 를 구성해야 합니다. [Elasticsearch 설치 및 구성](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/search/overview-search)을 참조하세요.

이 문서에서는 Elasticsearch 인덱스 상태가 &#39;*녹색*&#39;이(가) 아닌 경우에 대한 수정 사항을 제공합니다. &#39;*노란색*&#39;은(는) 일반을 나타내고 &#39;*빨간색*&#39;은(는) 잘못된 것을 나타냅니다. &#39;노란색&#39; 또는 &#39;빨간색&#39; 상태는 제품 누락 또는 이전 제품 정보 표시와 함께 발생할 수 있습니다.

## 영향을 받는 버전 및 제품

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## 문제

Elasticsearch 카탈로그 검색 색인이 느려 &#39;*녹색*&#39;이(가) 아닌 &#39;*노란색*&#39; 또는 &#39;*빨간색*&#39; 상태가 됩니다. 프론트엔드에서 변경 사항이 누락될 수도 있습니다.

## 원인

몇 가지 잠재적 원인이 있을 수 있습니다. Elasticsearch 인스턴스의 디스크 공간이 부족한 것이 한 가지 원인입니다. 또 다른 원인은 중복 인덱스입니다.

## 솔루션

다음 단계를 수행하기 전에 새 mysql 덤프를 생성하고 업무 시간 외에 수행하여 클라이언트에 영향을 주지 않도록 하십시오.

1. MySQL 검색으로 임시 전환 - MySQL 검색을 활성화합니다. (참고: Elasticsearch으로 다시 전환해야 합니다. 그렇지 않으면 성능 문제가 발생할 수 있습니다.)
1. 중복 인덱스를 식별하려면 다음 명령을 실행합니다.

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. 인덱스를 삭제하려면 다음을 수행하십시오.

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Elasticsearch을 다시 활성화합니다.
1. 전체 다시 색인을 실행합니다.
1. 다음 명령을 실행하여 인덱스 상태를 확인합니다.

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

이 단계가 작동하지 않으면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

## 관련 읽기

자세한 내용은 [Elasticsearch 클러스터 상태 API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html)를 참조하세요.
