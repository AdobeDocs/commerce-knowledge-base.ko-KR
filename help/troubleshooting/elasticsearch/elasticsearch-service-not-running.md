---
title: Elasticsearch 서비스가 실행되고 있지 않음
description: 이 문서에서는 ES(Elasticsearch) 서비스가 실행되고 있지 않을 때(일반적으로 충돌의 결과로) 발생할 수 있는 오류에 대한 솔루션을 제공합니다. curl을 사용하여 상태 검사를 실행할 때 발생하는 오류, 명령줄을 사용하여 색인 재지정, 예외 및 PHP 오류, 제품 페이지의 오류 등이 증상에 포함될 수 있습니다. 표에는 오류가 나열되며 오류를 해결하기 위한 리소스 링크가 있습니다. 하나의 증상은 다양한 원인을 가질 수 있습니다.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 3ff881f1c799201ed25ba9737864b1226d283c22
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Elasticsearch 서비스가 실행되고 있지 않음

이 문서에서는 ES(Elasticsearch) 서비스가 실행되고 있지 않을 때(일반적으로 충돌의 결과로) 발생할 수 있는 오류에 대한 솔루션을 제공합니다. curl을 사용하여 상태 검사를 실행할 때 발생하는 오류, 명령줄을 사용하여 색인 재지정, 예외 및 PHP 오류, 제품 페이지의 오류 등이 증상에 포함될 수 있습니다. 표에는 오류가 나열되며 오류를 해결하기 위한 리소스 링크가 있습니다. 하나의 증상은 다양한 원인을 가질 수 있습니다.

## Adobe Commerce과의 Elasticsearch 버전 호환성

* Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라:

   * v2.2.3+에서 ES 5.x 지원
   * v2.2.8+ 및 v2.3.1+에서 ES 6.x 지원
   * ES v2.x 및 v5.x는 다음과 같은 이유로 권장되지 않습니다. [서비스 종료](https://www.elastic.co/support/eol). 그러나 Adobe Commerce v2.3.1이 있고 ES 2.x 또는 ES 5.x를 사용하려는 경우 다음을 수행해야 합니다 [Elasticsearch php 클라이언트 변경](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).

* Magento Open Source v2.3.0+는 ES 5.x 및 6.x를 지원합니다(6.x가 권장됨).

<table>
<tr>
<th>ES 서비스가 실행되고 있지 않을 때의 증상</th>
<th>세부 사항</th>
<th>리소스</th>
</tr>
<tr>
<td rowspan="3">예외 오류</td>
</tr>
<tr>
<td>
<code>{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}]</code>
</td>
<td>
<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html">Elasticsearch 5가 구성되었지만 검색 페이지가 "Fielddata가 비활성화되었습니다..." 오류로 로드되지 않음</a> 을 참조하십시오.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Elasticsuite 인덱스를 삭제하지 않습니다.  다음을 참조하십시오 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite 추적 인덱스로 인해 Elasticsearch 문제가 발생합니다.</a> 을 참조하십시오.
 </td>
</tr>
<tr>
<td>PHP 오류</td>
<td>
<i>클러스터에서 활성 노드를 찾을 수 없음","1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>디스크 공간 부족에 대한 리소스:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">Linux 및 Unix 시스템 하드 디스크 문제 해결 팁 8 디스크 꽉 참 또는 디스크에 쓸 수 없음과 같은 문제</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfault: df에 따르면 디스크가 꽉 찼다고 되어 있지만 그렇지 않습니다.</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: Linux에서 디스크 공간이 사라진 위치를 추적하시겠습니까?</a></li>
<li>로그 파일이 충분히 정기적으로 보관되지 않습니다. 다음을 참조하십시오 <a href="https://docs.magento.com/m2/ee/user_guide/system/action-log-archive.html#configure-the-log-archive">로그 아카이브 구성</a> 개발자 설명서에서 확인할 수 있습니다.</li>
<li>파일 시스템 디렉토리가 최적화되지 않았습니다. 다음을 참조하십시오 <a href="https://docs.magento.com/m2/ee/user_guide/system/file-optimization.html">파일 최적화</a> 개발자 설명서에서 확인할 수 있습니다.</li>
<li>위의 설명서에 나와 있는 해결 방법으로 문제가 해결되지 않으면 Adobe 계정 팀에 연락하여 추가 스토리지를 요청하는 것이 좋습니다.</li>
</ul>
</li>
<li>디스크에 스토리지가 부족하지 않지만 왼쪽 열에 오류 메시지가 계속 나타나는 경우 <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">지원 티켓 제출</a>.</li>
</ul>
<ul>
<li>다음을 참조하십시오 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite 추적 인덱스로 인해 Elasticsearch 문제가 발생합니다.</a> 을 참조하십시오.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> 오류</td>
<td>실행 <code>curl</code> Elasticsearch 상태를 확인하는 명령:<code>curl -m1 localhost:9200/_cluster/health?pretty</code>(또는<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>스타터 계정의 경우) 이 오류가 발생합니다. <i>오류: curl: (7) localhost port 9200에 연결하지 못했습니다. 연결이 거부되었습니다.</i> </td>
</tr>
<tr>
<td>명령줄 오류</td>
<td>실행 중 <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> 이 오류를 생성합니다. <i>카탈로그 검색 인덱서 프로세스 알 수 없는 오류: 클러스터에 활성 노드가 없습니다.</i>
</td>
</tr>
<tr>
<td>제품 페이지 오류
</td>
<td><i>요청을 처리하는 도중 오류가 발생했습니다.
      보안상의 이유로 기본적으로 예외 인쇄가 비활성화되어 있습니다.</code></i>
</tr>
</table>
