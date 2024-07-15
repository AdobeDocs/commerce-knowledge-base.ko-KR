---
title: Adobe Commerce에서 New Relic을 사용하여 성능 문제 해결
description: '이 문서에서는 New Relic을 사용하여 Adobe Commerce에서 클라우드 인프라 성능 문제를 해결하는 문제 해결 단계를 제공합니다. 추가 정보를 위한 리소스도 제공합니다. 다음은 문제 목록입니다. 지원 기술 자료에서 문제 해결 단계를 보려면 클릭하십시오.'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Adobe Commerce에서 New Relic을 사용하여 성능 문제 해결

이 문서에서는 New Relic을 사용하여 Adobe Commerce에서 클라우드 인프라 성능 문제를 해결하는 문제 해결 단계를 제공합니다. 추가 정보를 위한 리소스도 제공합니다. 아래 표에서 권장되는 리소스와 관련하여 다룬 다음 문제는 다음과 같습니다.

* 낮은 Apdex 점수
* 높은 CPU 사용량
* 높은 입출력 작업
* 중단

<table>
<tbody>
<tr>
<td>문제</td>
<td>문제 해결</td>
<td>리소스</td>
</tr>
<tr>
<td>
<p>낮은 Apdex 점수:</p>
<p>New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex 점수</a>는 웹 응용 프로그램 및 서비스의 응답 시간에 대한 사용자의 만족도를 측정합니다.</p>
</td>
<td>
<p><a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; 개요에 로그인합니다. 개요 페이지의 오른쪽에 Apdex 점수 그래프가 표시됩니다. Apdex 점수가 0.5 이하이면 우려되는 지점이며 조사를 보증합니다. 웹 트랜잭션 시간(서버 요청):</p>
<ol>
<ol>
<li><a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (앱 선택) &gt; 개요에 로그인합니다. 기본 차트 드롭다운 필터에서 필터가 웹 트랜잭션 시간으로 설정되어 있는지 확인합니다. 아래의 트랜잭션 표에서 앱 서버 시간을 찾습니다. 오래 실행되거나 의심스러운 트랜잭션이 있는지 확인합니다.</li>
<li>모니터링 &gt; 트랜잭션으로 이동하여 개별적으로 조사한 후 웹 및 가장 많은 시간이 드는 <em>에 대한 필터를 설정해야 합니다.</em>
</li>
<li>그런 다음 리소스를 사용하는 결제 기관, ERP 등의 타사 모듈을 검색합니다.</li>
<li>APM의 모니터링 섹션에서 다음을 수행합니다.<ol>
<li>트랜잭션을 누릅니다.</li>
<li>아래로 스크롤하여 모든 트랜잭션 표시 테이블을 누릅니다.</li>
<li><a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">다양한 매개 변수</a>별로 트랜잭션을 정렬하고 의심이 드는 항목으로 이동할 수 있습니다.</li>
<li>Apdex 점수가 낮거나, 이례적으로 높은 카운트 또는 높은 평균 시간 또는 불일치 %가 있는 거래를 검토합니다.</li>
<li>각 개별 트랜잭션을 클릭합니다. 문제를 해결할 수 없는 경우 <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">지원 티켓을 제출합니다.</a>
</li>
<li>추가 조사가 필요한 경우 웹이 아닌 트랜잭션을 확인하는 것이 좋습니다.</li>
</ol>
</li>
</ol>
</ol>
<p>웹 트랜잭션이 아닌 시간(작업 및 백그라운드 작업):</p>
<ol>
<ol>
<li><a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (앱 선택) &gt; 개요에 로그인합니다. 기본 그래프 드롭다운 필터에서 웹이 아닌 트랜잭션 시간 을 선택해야 합니다. 트랜잭션 테이블에서 개별 트랜잭션을 누릅니다. 오래 지속되거나 의심스러운 거래를 찾습니다. 여기에는 서드파티를 포함한 백엔드 작업, cron 작업 또는 가져오기/내보내기 작업이 포함됩니다.</li>
</ol>
</ol>
</td>
<td>
<p>New Relic Apdex 점수에 대한 자세한 내용은 <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">New Relic 설명서 &gt; APM Apdex &gt; 사용자 만족도 측정</a>을 참조하십시오. 지원 기술 자료에서 <a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Adobe Commerce에 대한 관리 경고: Apdex 경고 경고</a>를 참조할 수도 있습니다.</p>
</td>
</tr>
<tr>
<td>
<p>높은 CPU 사용량:</p>
<p>높은 CPU 사용률은 MySQL, Redis 등과 같이 특히 사용량이 많은 서비스가 있음을 나타낼 수 있습니다.</p>
</td>
<td>
<ol>
<li><a href="https://login.newrelic.com/login">New Relic</a> &gt; 인프라 &gt; 프로세스에 로그인합니다.</li>
<li>CPU 그래프를 검토하여 100% 이상의 CPU 시간을 사용하는 정지 또는 소모 높은 프로세스가 있는지 확인하고 인스턴스의 프로세서 카운트와 비교합니다. 자원 활용도가 최고점에 달할 수 있도록 주의를 기울여야 합니다. 중단된 크론이 아닌 경우 프로세스를 종료하지 않는 것이 좋습니다.</li>
</ol>
</td>
<td>
<p>성능 지표(특히 개별 또는 프로세스 그룹의 CPU 백분율, I/O 바이트 및 메모리 사용량)에 대한 자세한 내용은 <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">New Relic 설명서 &gt; 인프라 UI 페이지 &gt; 인프라 호스트 페이지 &gt; 프로세스 탭</a>을 참조하십시오.</p>
</td>
</tr>
<tr>
<td>
<p>높은 I/O 작업: 각 고객의 경우 이 숫자는 개인이지만 평균과 크게 다릅니다.</p>
</td>
<td>
<p>이전의 평균 입출력 작업에 비해 비정상적인 급등을 찾아보십시오.</p>
<ol>
<li><a href="https://login.newrelic.com/login">New Relic</a> &gt; 인프라 &gt; 프로세스에 로그인합니다.</li>
<li>I/O Read Bytes Per Second 그래프를 검토합니다.</li>
<li>스파이크 시간을 기록합니다.</li>
<li>APM을 클릭합니다.</li>
<li>기본 그래프 드롭다운 필터에서 웹 트랜잭션 시간 을 선택해야 합니다.</li>
<li>기록한 스파이크 시간에 대한 시간을 설정합니다.</li>
<li>높은 I/O 작업을 발생시킨 트랜잭션을 검색합니다.</li>
<li>각 트랜잭션 추적 &gt; 추적 세부 정보를 드릴다운하여 문제를 일으킬 수 있는 요인을 찾습니다.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>중단: New Relic은 Apdex를 통해 중단을 결정합니다. Apdex 점수 그래프에 중단으로 간주되는 Apdex &lt; 0.4를 나타내는 빨간색 줄이 표시됩니다.</p>
</td>
<td>
<p>중단을 조사하려면 웹 및 비웹 트랜잭션, 데이터베이스 및 타사 트랜잭션을 검사하는 몇 가지 단계를 수행해야 합니다. 웹 트랜잭션:</p>
<ol>
<li><a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; 개요에 로그인합니다. 드롭다운 그래프 필터에서 필터가 웹 트랜잭션 시간으로 설정되어 있는지 확인합니다.</li>
<li>수동으로 시간 창의 범위를 좁힙니다.</li>
<li>트랜잭션을 누릅니다. 필터가 웹으로 설정되어 있고 가장 많은 시간이 소요되는지 확인하십시오. 가장 오래 실행되는 트랜잭션을 조사합니다.</li>
<li>추가 조사가 필요한 경우 웹이 아닌 트랜잭션을 확인하는 것이 좋습니다.</li>
</ol>
<p>비웹 트랜잭션:</p>
<ol>
<li>개요 페이지로 돌아가서 드롭다운 필터에서 비웹 트랜잭션으로 전환합니다.</li>
<li>페이지 맨 아래에 있는 트랜잭션 추적을 하나씩 검토합니다.</li>
<li>문제에 따라 PHP 프로파일러와 같은 서드파티 도구를 사용하여 병목 지점을 찾아야 할 수도 있습니다.</li>
<li>추가 조사가 필요한 경우 데이터베이스 프로세스를 검토하는 것이 좋습니다.</li>
</ol>
<p>데이터베이스 프로세스:</p>
<ol>
<li>APM 페이지에서 모니터링 &gt; 데이터베이스로 이동합니다.</li>
<li>가장 시간이 많이 걸리는 항목별로 정렬합니다.</li>
<li>상위 쿼리를 검토합니다.

참고: <code>업데이트</code> 또는 <code>삽입</code>쿼리는 CPU를 가장 많이 사용하는 쿼리입니다.</li>
<li>정렬 기준 선택기에서 처리량으로 전환하고 데이터베이스 처리량이 드롭다운된 프로세스를 찾습니다.</li>
<li>추가 조사가 필요한 경우 서드파티 서비스를 검토하는 것이 좋습니다.</li>
</ol>
<p>타사 서비스:</p>
<ol>
<li>APM 페이지에서 모니터링 &gt; 외부 서비스로 이동합니다.</li>
<li>정렬 기준 드롭다운 목록에서 가장 느린 평균 응답 시간을 선택합니다.</li>
<li>중단 직전에 발생한 프로세스를 찾습니다.</li>
</ol>
</td>
<td>
<p>특정 성능 문제를 조사하는 방법에 대한 자세한 내용은 <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">New Relic 설명서 &gt; APM UI 페이지 &gt; 트랜잭션 페이지 &gt; 드릴다운 기능 사용</a>을 참조하십시오.</p>
</td>
</tr>
</tbody>
</table>
