---
title: 클라우드 인프라의 Adobe Commerce에서 New Relic 문제 해결
description: 이 문서에서는 클라우드 인프라에서 Adobe Commerce의 New Relic 문제를 해결하는 데 필요한 리소스를 제공합니다.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에서 New Relic 문제 해결

이 문서에서는 클라우드 인프라에서 Adobe Commerce의 New Relic 문제를 해결하는 데 필요한 리소스를 제공합니다.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>문제</strong></td>
<td class="wysiwyg-text-align-center"><strong>원인</strong></td>
<td class="wysiwyg-text-align-center"><strong>리소스</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">액세스 문제</td>
</tr>
<tr>
<td>
<p><u>New Relic에서 프로젝트를 볼 수 없습니다.</u></p>
<p><em>New Relic</em>에 로그인했지만 보기/액세스 권한이 있는 프로젝트를 볼 수 없습니다.</p>
</td>
<td>
<p>이러한 경우 관리자는 사용자를 프로젝트에 추가해야 합니다.</p>
</td>
<td>
<p>지원 기술 자료에서 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">New Relic 서비스에 액세스</a>.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">데이터 문제</td>
</tr>
<tr>
<td>
<p><u>설치 후 데이터가 누락되었습니다.</u></p>
<p><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic 진단 유틸리티</a>를 사용하여 원인을 식별하십시오. 도움이 되지 않는 경우 에이전트별 솔루션을 확인하십시오. 이러한 솔루션이 포함된 문서에 대한 링크는 오른쪽 열에 있습니다.</p>
</td>
<td>
<p>데이터 누락의 원인은 다를 수 있습니다. 다음을 수행해야 합니다.</p>
<ul>
<li>에이전트가 설치되었는지 확인합니다.</li>
<li>앱 이름 및 라이선스 키를 확인합니다.</li>
<li>웹 서버를 다시 시작합니다.</li>
<li>시스템이 호환성 요구 사항을 충족하는지 확인합니다.</li>
<li>INI 설정.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">New Relic 설명서 &gt; APM 에이전트 &gt; 데이터 보기 안 함</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">New Relic 설명서 &gt; New Relic 브라우저 &gt; 데이터 보기 안 함</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">New Relic 설명서 &gt; New Relic 인프라 &gt; 데이터 보기 안 함</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">New Relic 설명서 &gt; New Relic 모바일 &gt; 데이터 보기 안 함</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>트랜잭션 타임스탬프 불일치.</u> New Relic UI를 사용하여 긴 트랜잭션(5분 이상)을 찾기 어려울 수 있습니다. 예상 시간대 외부에 표시되는 트랜잭션을 찾을 수도 있습니다.</p>
</td>
<td>
<p>New Relic UI에는 트랜잭션이 시작된 시간이 아니라 트랜잭션 종료 시간이 표시됩니다.</p>
</td>
<td>
<p>New Relic UI를 사용하여 거래 시작을 계산하려면 거래 기간을 확인하십시오. New Relic UI에서 제공한 타임스탬프(트랜잭션 종료)에서 기간 금액을 뺍니다.</p>
</td>
</tr>
<tr>
<td>
<p><code>|</code> 및 <code>%</code>과(와) 같은 특수 문자를 사용하는 <u>NerdGraph GraphQL <code>curl</code> 쿼리가 작동하지 않습니다</u>.</p>
</td>
<td>
<p>NerdGraph 내의 New Relic "curl로 복사" 기능은 현재 <code>|</code> 및 <code>%</code>과(와) 같은 특수 문자를 처리하는 방법을 제공하지 않습니다.</p>
</td>
<td>
<p>다른 API 라이브러리를 사용하여 특수 문자로 문제를 해결합니다. 예를 들어 Python의 Graphql API용 GraphQLClient 라이브러리 또는 Java 언어 호출별 Apache.commons입니다. <a href="https://graphql.org/code/">GraphQL</a>에서 클라이언트 라이브러리를 검토하십시오.</p>
</td>
</tr>
<tr>
<td>
<p><u>차트 및 대시보드 표시 문제</u></p>
</td>
<td>
<p>New Relic 도메인을 허용 목록에 추가하거나 문제를 일으키는 브라우저 확장을 제거하여 누락된 차트를 해결합니다.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">New Relic 설명서 &gt; 차트가 없거나 렌더링되지 않음</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">PHP 에이전트 문제</td>
</tr>
<tr>
<td>
<p><u>PHP 에이전트가 올바른 인스턴스 수를 표시하지 않습니다.</u></p>
</td>
<td>
<p>백엔드 프로세스와 처리량에 따라 인스턴스 수가 늘어날 수 있습니다. 서버 값 간의 차이는 한 서버에서 실행 중인 프로세스로 인해 발생할 수 있지만 다른 서버에서는 발생하지 않습니다.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">New Relic 설명서 &gt; PHP 에이전트 인스턴스 수 문제 해결</a> </p>
</td>
</tr>
</tbody>
</table>
