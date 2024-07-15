---
title: 'Adobe Commerce의 관리 경고: CPU 위험 경고'
description: 이 문서에서는 New Relic에서 Adobe Commerce에 대한 CPU 위험 경고를 수신하는 경우의 문제 해결 단계를 제공합니다. 문제를 해결하기 위해 즉각적인 조치가 필요합니다. 선택한 경고 알림 채널에 따라 경고는 다음과 같이 표시됩니다.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 5be8f2969426078bfcc0e4ffb4895dcf0327165f
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Adobe Commerce에 대한 관리 경고: CPU 위험 경고

이 문서에서는 New Relic에서 Adobe Commerce에 대한 CPU 위험 경고를 수신하는 경우의 문제 해결 단계를 제공합니다. 문제를 해결하기 위해 즉각적인 조치가 필요합니다. 선택한 경고 알림 채널에 따라 경고는 다음과 같이 표시됩니다.

![디스크 중요 경고](assets/cpu-critical-magento-managed.png){width="500"}

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure Pro 계획 아키텍처

## 문제

[Adobe Commerce에 대한 관리 경고](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)에 등록했으며 경고 임계값 중 하나 이상을 초과한 경우 New Relic에서 관리 경고를 받게 됩니다. 이러한 경고는 지원 및 엔지니어링의 인사이트를 사용하여 고객에게 표준 세트를 제공하기 위해 Adobe Commerce에서 개발했습니다.

<u>**실행!**</u>:

* 이 경고가 지워질 때까지 예약된 배포를 중단합니다.
* 사이트가 응답하지 않거나 완전히 응답하지 않는 경우 즉시 사이트를 유지 관리 모드로 전환합니다. 단계는 개발자 설명서에서 [설치 안내서 > 유지 관리 모드 활성화 또는 비활성화](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten)를 참조하십시오. 문제 해결을 위해 사이트에 계속 액세스할 수 있도록 제외 IP 주소 목록에 IP를 추가해야 합니다. 단계는 개발자 설명서에서 [제외 IP 주소 목록 유지](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt)를 참조하십시오.

<u>**안 함!**</u>:

* 사이트에 추가 페이지 보기를 가져올 수 있는 추가 마케팅 캠페인을 시작합니다.
* 인덱서 또는 추가 크론을 실행하여 CPU 또는 디스크에 추가 스트레스를 발생시킬 수 있습니다.
* 주요 관리 작업(예: Commerce 관리, 데이터 가져오기/내보내기)을 수행합니다.
* 캐시를 지웁니다.

경고 원인을 조사하고 해결하기 전에 &quot;안 함&quot; 작업을 수행하면 사이트가 응답하지 않을 수 있습니다(아직 사이트 중단이 발생하지 않은 경우).

## 솔루션

다음 단계에 따라 원인을 식별하고 해결하십시오.

>[!WARNING]
>
>이 경고는 중요한 경고이므로 문제를 해결하기 전에 **1**&#x200B;단계를 완료하는 것이 좋습니다(2단계 이상).

Adobe Commerce 지원 티켓이 있는지 확인합니다. 단계는 지원 기술 자료에서 [지원 티켓 추적](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)을 참조하세요. 지원 팀이 New Relic 임계값 경고를 받고, 티켓을 만들고, 문제 해결을 시작했을 수 있습니다. 티켓이 없으면 만듭니다. 티켓에는 다음 정보가 있어야 합니다.

1. 연락처 이유: &quot;New Relic CRITICAL 경고 수신됨&quot;을 선택합니다.
1. 경고에 대한 설명.
1. [New Relic 문제 링크](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). [Adobe Commerce에 대한 관리 경고](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)에 포함되어 있습니다.
1. 성능 문제가 있는 트랜잭션을 식별하려면 [New Relic APM의 트랜잭션 페이지](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)를 사용하십시오.
   * 오름차순 Apdex 점수를 기준으로 트랜잭션을 정렬합니다. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)은(는) 웹 응용 프로그램 및 서비스의 응답 시간에 대한 사용자 만족도를 나타냅니다. [낮은 Apdex 점수](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md)는 병목 현상(응답 시간이 더 긴 트랜잭션)을 나타낼 수 있습니다. 일반적으로 데이터베이스, Redis 또는 PHP와 관련되어 있습니다. 단계는 New Relic [Apdex 불만족도가 가장 높은 트랜잭션 보기](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)를 참조하십시오.
   * 가장 높은 처리량, 가장 느린 평균 응답 시간, 가장 많은 시간이 소요되는 임계값 및 기타 임계값별로 트랜잭션을 정렬합니다. 단계는 New Relic [특정 성능 문제 찾기](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)를 참조하십시오.
1. 여전히 원본 식별이 어려운 경우 [New Relic APM의 인프라 페이지](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page)를 사용하여 리소스 사용량이 많은 서비스를 식별하십시오. 단계는 New Relic [인프라 모니터링 호스트 페이지 > 프로세스 탭](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)을 참조하십시오.
1. 소스를 식별하는 경우 SSH를 환경에 추가하여 자세히 조사하십시오. 단계는 개발자 설명서에서 [클라우드 인프라의 Adobe Commerce 환경에 대한 SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)를 참조하십시오.
1. 여전히 소스 식별이 어려운 경우:
   * 최근 코드 배포 또는 구성 변경(예: 새로운 고객 그룹 및 카탈로그에 대한 큰 변경)과 관련된 문제를 식별하려면 최근 트렌드를 검토하십시오. 코드 배포 또는 변경 시 상관 관계에 대한 지난 7일간의 활동을 검토하는 것이 좋습니다.
   * 플랫 카탈로그를 확인하고 비활성화하는 것이 좋습니다. 단계는 지원 기술 자료에서 [느린 성능, 느리고 오래 실행되는 크론](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)을 참조하세요.
   * DDoS 공격이 있다고 의심되는 경우 보트 트래픽을 차단해 보십시오. 단계는 지원 기술 자료에서 [Fastly 수준의 클라우드 인프라에서 Adobe Commerce에 대한 악성 트래픽을 차단하는 방법](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md)을 참조하세요.
1. 일시적인 문제인 경우 업사이드와 같은 완화 단계를 수행하거나 사이트를 유지 관리 모드로 전환합니다. 단계는 지원 기술 자료에서 [임시 크기 조정 요청 방법](/help/how-to/general/how-to-request-temporary-magento-upsize.md) 및 개발자 설명서에서 [설치 안내서 > 유지 관리 모드 활성화 또는 비활성화](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten)를 참조하십시오. 업사이징이 사이트를 정상 작업으로 되돌리는 경우 영구적인 업사이징을 요청하거나(Adobe 계정 팀에 문의) 부하 테스트를 실행하고 서비스에 대한 압력을 줄이는 쿼리 또는 코드를 최적화하여 전용 스테이징에서 문제를 재현해 보십시오. 단계는 클라우드 인프라의 Adobe Commerce 개발자 설명서에서 [테스트 배포 > 부하 및 스트레스 테스트](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest)를 참조하십시오.
