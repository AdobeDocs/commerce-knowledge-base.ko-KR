---
title: 'Fastly에서 제공하는 웹 애플리케이션 방화벽(WAF): FAQ'
description: WAF(Web Application Firewall)는 보안 규칙 세트에 대해 트래픽을 필터링하여 악성 트래픽이 사이트 및 네트워크로 유입되는 것을 방지합니다. 규칙을 트리거하는 트래픽은 사이트 또는 네트워크를 손상시키기 전에 차단됩니다.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Fastly에서 제공하는 웹 애플리케이션 방화벽(WAF): FAQ

## Adobe Commerce의 관리 클라우드 WAF(Fastly에서 제공)는 어떻게 작동합니까?

WAF(Web Application Firewall)는 보안 규칙 집합에 대해 트래픽을 필터링하여 [악성 트래픽](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md)이 사이트 및 네트워크로 들어오는 것을 방지합니다. 규칙을 트리거하는 트래픽은 사이트 또는 네트워크를 손상시키기 전에 차단됩니다.

Adobe Commerce의 클라우드 WAF은 WAF 웹 애플리케이션을 광범위한 공격으로부터 보호하기 위해 고안된 규칙 세트와 함께 Adobe Commerce 정책을 제공합니다.

WAF은 웹 및 관리자 트래픽을 검사하여 의심되는 활동이 있는지 확인합니다. GET 및 POST 트래픽(HTTP API 호출)을 평가하고 규칙 세트를 적용하여 차단할 트래픽을 결정합니다. WAF은 SQL 삽입 공격, 크로스 사이트 스크립팅 공격, 데이터 내보내기 공격, HTTP 프로토콜 위반 등 다양한 공격을 차단할 수 있습니다.

클라우드 기반 서비스로서 WAF은 설치 또는 유지 관리할 하드웨어나 소프트웨어가 필요하지 않습니다. 기존 기술 파트너인 Fastly는 소프트웨어와 전문 지식을 제공합니다. 항상 가동되는 고성능 WAF은 Fastly의 글로벌 게재 네트워크의 각 캐시 노드에 있습니다.

## 모든 클라우드 고객이 WAF을 사용할 수 있습니까?

예. 클라우드 WAF 서비스는 Adobe Commerce on cloud infrastructure 시작 계획 아키텍처 및 Adobe Commerce on cloud infrastructure Pro 계획 아키텍처 계획 모두에 대한 Adobe Commerce on cloud infrastructure 구독에 추가 비용 없이 포함됩니다. WAF 서비스는 프로덕션 및 스테이징 환경에서 사용할 수 있습니다.

## WAF이 PCI DSS 6.6 요구 사항을 준수합니까?

예.

## 클라우드 인프라 계정의 Adobe Commerce이 여러 도메인의 사이트를 관리하는 경우 WAF 프로필이 각 도메인에 대해 조정됩니까? 아니면 모든 도메인에 대해 총괄적으로 조정됩니까?

WAF은 단일 클라우드 계정의 모든 도메인에 대해 전체적으로 조정됩니다.

## WAF에는 어떤 규칙이 사용됩니까?

클라우드 인프라 프로덕션 환경에서 Adobe Commerce에 적용되는 WAF 프로필에 설정된 규칙은 웹 서비스에 대한 일반적인 악용을 다루는 OWASP Top 10 Threat Protection 규칙 세트를 기반으로 합니다. 여기에는 TrustWave SpiderLabs에서 개발한 Adobe Commerce 관련 규칙도 포함되어 있습니다. Fastly의 보안 연구 팀은 잘못된 IP 주소, 잘못된 사용자 에이전트, 알려진 봇넷 명령 및 제어 노드 등 일반적으로 알려진 공격으로부터 사이트 및 네트워크를 보호하는 규칙을 추가했습니다. 높은 보안 범위를 제공하는 OWASP Paranoia Level 3 이하의 규칙을 활성화합니다.

## 로그에 액세스하려면 어떻게 합니까?

로그를 로깅 도구로 보내려면 TAM(기술 계정 관리자)과 함께 로깅 엔드포인트를 Fastly로 추가하십시오.

## 블록 요청은 어떻게 표시됩니까?

차단된 요청은 요청 식별자가 있는 403 페이지를 반환합니다.

사용자 지정에 요청 식별자가 포함되어 있으면 이 페이지를 사용자 지정할 수 있습니다. 자세한 내용은 기술 계정 관리자에게 문의하십시오.

## WAF 규칙 세트를 어떻게 업데이트합니까? WAF 규칙을 얼마나 빨리 변경 또는 업데이트하여 프로덕션에서 전역적으로 적용할 수 있습니까?

클라우드 WAF 서비스의 일부로, Fastly는 상업용 서드파티, Fastly 리서치 및 오픈 소스의 규칙 업데이트를 관리합니다. 필요에 따라 또는 해당 소스에서 규칙 변경 내용을 사용할 수 있을 때 게시된 규칙을 정책으로 업데이트합니다. 게시된 규칙 클래스와 일치하는 새 규칙은 활성화되면 모든 서비스의 WAF 인스턴스에도 삽입됩니다. 이를 통해 새롭거나 진화하는 활용에 대한 즉각적인 보장이 보장됩니다. Fastly 설명서 사이트에서 [규칙 업데이트 및 유지 관리에 대한 정보](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance)를 검토할 수 있습니다.

## Adobe Commerce의 클라우드 WAF은 직접 고객에게 Fastly가 제공하는 WAF 솔루션과 어떻게 다릅니까?

Fastly에서 직접 판매하는 WAF 솔루션은 광범위한 규칙 세트와 규칙 사용자 지정 및 맬웨어 보호와 같은 추가 기능을 포함하는 유료 제품입니다. Adobe Commerce의 클라우드 WAF 솔루션에는 Adobe Commerce 애플리케이션을 대상으로 하는 규칙의 하위 집합이 포함되어 있으며 각 고객의 프로덕션 환경에 대해 하나의 규칙 집합만 포함됩니다.

## WAF이 어떤 유형의 보안 위협으로부터 보호합니까?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">위협</th>
<th style="width: 497.5px; text-align: left;">WAF 보호</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">SQL 삽입 공격</td>
<td style="width: 497.5px;">OWASP ModSecurity 핵심 규칙 세트와 TrustWave 상용 규칙 세트 모두 SQL 주입 공격과 그 변형에 대한 특정 필터를 포함합니다.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>교차 부위 주사</p>
</td>
<td style="width: 497.5px;">OWASP 규칙 세트는 교차 사이트 삽입 공격으로부터 보호합니다. Fastly는 각 요청에 대해 채점 메커니즘을 활용하여 사이트 간 주입 및 원본에 대한 기타 위협을 찾습니다. 전체 핵심 규칙 세트에 대해 모든 요청에 점수를 매기고 요청 점수가 구성 가능한 임계값 미만인지 확인합니다.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">브루트 포스 공격</td>
<td style="width: 497.5px;">OWASP 규칙 세트가 적용됩니다. 또한 Fastly는 특정 소스, 요청을 인식하거나 원본 데이터 센터에 도달하기 전에 강제로 적용하거나 보안 제어를 압도하려고 시도하는 VCL 코드를 사용하여 강제 적용 활동을 차단합니다.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">네트워크 공격</td>
<td style="width: 497.5px;">네트워크 공격 또는 네트워크 인프라를 대상으로 하는 공격은 Fastly에서 자동으로 관리합니다. Fastly는 DNS를 원본으로 전달하지 않으며 좁은 HTTP, HTTPS 또는 DNS 프로필과 일치하지 않는 트래픽은 네트워크 가장자리에서 삭제됩니다. 제어 프로토콜을 타깃팅하는 공격은 네트워크 전체에서 엔드포인트의 인증을 통해 방어됩니다. 또한 Fastly 네트워크 내에서 사용되는 네트워크 프로토콜은 증폭 또는 반영 수단으로 활용할 수 없도록 강화됩니다. 고객은 CDN 서비스의 구성 요소로 고객에게 게시된 Fastly 캐시 IP 주소 공간을 활용하여 Fastly 네트워크를 우회하는 공격으로부터 보호할 책임이 있습니다. 우회 공격이 이러한 주소를 대상으로 사용할 수 없도록 원본 IP 주소 공간을 공용 DNS에 게시하지 않는 것이 좋습니다.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">JavaScript 주사 발작</td>
<td style="width: 497.5px;">WAF 규칙은 웹 서비스가 있는 클라이언트 통신에 악의적인 JavaScript 코드가 삽입되지 않도록 보호합니다. 일반적인 익스플로잇 패턴 또는 점수는 WAF을 통해 필터링되어 원본 서비스의 무결성을 보장합니다.</td>
</tr>
</tbody>
</table>

## 추가 기능과 기능이 제공됩니까?

Adobe Commerce의 WAF 서비스에는 PCI 요구 사항의 일부로서 OWASP Top-10 위협에 대한 보호, 긍정 오류(false positive)에 대한 등급을 포함한 24x7 지원, 버전 업그레이드가 포함됩니다. 다음 기능은 표준 오퍼에서 지원되지 않습니다.

* 속도 제한
* 규칙 사용자 지정
* 보트 완화
* 맬웨어 보호

## 사이트 성능이 WAF의 영향을 어떻게 받습니까?

캐싱되지 않은 모든 요청에는 예상 1.5밀리초(ms)~20ms의 지연이 도입됩니다.

## 고객이 IP 블랙리스트를 만들고 수정하여 트래픽을 차단할 수 있습니까?

예. 고객은 클라우드 인프라의 관리 UI에 있는 Adobe Commerce에서 국가별 및 액세스 제어 목록(ACL)별로 차단을 활성화할 수 있습니다. 특정 국가나 특정 IP 또는 IP 범위에서 온 방문자에 대한 액세스를 차단하려는 경우에 이러한 기능을 사용하십시오. 차단된 방문자에게 오류 코드가 아닌 사용자 지정 페이지가 표시되도록 하려면 Fastly 구성 메뉴에서 HTML을 업로드하여 사용자 지정 오류 페이지를 만들 수 있습니다. 개발자 설명서에서 [사용자 지정 오류/유지 관리 페이지 만들기](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)를 참조하십시오.

## 내 WAF 서비스의 운영 상태를 확인하려면 어디로 해야 합니까?

전체 WAF 서비스 가용성은 [Fastly 상태 페이지](https://status.fastly.com/)에서 보고됩니다. 개별 고객의 WAF에 대한 가용성 보고가 제공되지 않습니다.

## Adobe Commerce에서 WAF 서비스에 대한 인시던트 관리를 제공합니까?

현재 사고 관리는 제공되지 않습니다.

## Adobe Commerce에 보안 운영 센터가 있습니까?

Adobe Commerce에는 보안 운영 센터가 없지만, 실시간으로 보안 사고에 대응할 수 있는 적절한 리소스를 확보할 수 있는 보안 운영 프로세스가 있습니다. 또한 연중무휴 24시간 Follow-the-sun 지원을 제공합니다.

[보안 센터](https://helpx.adobe.com/security.html)에서 Adobe Commerce 관련 보안 뉴스 및 업데이트를 받을 수도 있습니다.

## 어떤 지원이 제공됩니까?

WAF 지원은 원치 않는 요청 또는 악의적인 요청의 서비스 영향을 완화하는 데 도움이 되는 다음 리소스를 제공합니다.

* 온보딩: Adobe Commerce 관리 클라우드 WAF을 지원하는 Fastly 서비스의 활성화, 초기 설정 및 제한된 모니터링
* WAF이 합법적인 트래픽을 차단하는 인스턴스를 해결하기 위해 진행 중인 긍정 오류(false positive) 트리거
* WAF 버전 업그레이드의 일부로 도입된 새 표준 규칙 구성

심각도 정의, 응답 시간, 채널 및 가용성을 포함한 추가 지원 정보는 [Cloud SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) 용어를 참조하십시오.

## WAF이 합법적인 트래픽을 차단하거나 다른 문제를 야기하는 경우 어떻게 도움을 받을 수 있습니까?

[Adobe Commerce 도움말 센터](https://support.magento.com)에서 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). 티켓이 WAF 서비스와 관련되어 있음을 나타내고 차단된 요청 ID(ID)를 포함하십시오.

Adobe Commerce 지원 티켓 시스템은 지원 엔지니어와 고객 담당자 간의 커뮤니케이션을 추적합니다. 이 시스템은 타임스탬프가 있는 통신 대본을 제공하고, 티켓이 업데이트되면 고객 및 Adobe Commerce 직원에게 이메일을 전송합니다.

온라인에 제출된 모든 인시던트에 대해 Adobe Commerce 고객 지원 센터 티켓 시스템을 통해 인시던트 수령증을 확인합니다. 적절하게 제출된 사고 접수 시 위에 명시된 우선 순위 수준에 따라 지원 서비스가 우선 순위를 갖습니다.

다음 표에는 WAF 지원에 대한 지원 채널 및 가용성이 요약되어 있습니다.

<table class="table-basic">
<tbody>
<tr>
<th>지원 서비스</th>
<th>세부 사항</th>
</tr>
<tr>
<td>온라인 셀프서비스 도움말</td>
<td>무제한 액세스</td>
</tr>
<tr>
<td>문제 보고서 가용성</td>
<td>24/7</td>
</tr>
<tr>
<td>웹 포털</td>
<td>Zendesk를 통해 제공</td>
</tr>
<tr>
<td>긴급 에스컬레이션*</td>
<td>미국 및 국제 번호에 대해서는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html">Adobe Commerce P1 알림 핫라인</a> 문서를 참조하세요.</td>
</tr>
</tbody>
</table>

*\* Adobe Commerce의 무료 지원 전화선은 우선 순위 1 인시던트에 대해서만 예약되어 있습니다. 우선 순위가 아닌 1 호출은* 문제에 대한 전반적인 응답을 느리게 합니다.

## 긍정 오류(false positive)는 어떻게 평가됩니까?

합법적인 요청이 WAF 규칙을 트리거한 인스턴스를 빠르게 해결하고 해결하기 위한 가양성 평가 프로세스(24x7 사용 가능)가 있습니다. 긍정 오류(False positive) 이벤트는 우선 순위 1 문제로 처리됩니다. 기본 작업으로 지원 팀은 WAF 정책을 즉시 업데이트하여 차단 이벤트를 트리거한 규칙을 비활성화하고 합법적인 요청이 WAF을 통과하도록 허용할 수 있습니다.

## 클라우드 인프라 사이트에서 Adobe Commerce의 관리 섹션에 대한 트래픽이 WAF 규칙을 트리거하는 경우 어떻게 합니까? Adobe Commerce 지원에서 차단된 관리자 트래픽의 문제를 해결합니까?

예. 차단된 관리자 트래픽은 우선 순위 1 문제로 처리됩니다.
