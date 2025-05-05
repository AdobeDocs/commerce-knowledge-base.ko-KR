---
title: Adobe Commerce의 max_allowed_packet 관련 데이터베이스 오류
description: 이 문서에서는 'var/log/exception.log'에서 대량의 제품을 가져오거나 서버에서 기본값인 16MB보다 큰 'max_allowed_packet'에 설정된 보다 큰 패킷을 처리하도록 하는 작업을 수행할 때 발생할 수 있는 데이터베이스 연결 오류에 대한 해결 방법을 제공합니다.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Adobe Commerce의 max_allowed_packet 관련 데이터베이스 오류

이 문서에서는 많은 수의 제품을 가져오거나 서버에서 기본값인 16MB보다 큰 `max_allowed_packet`에 설정된 것보다 큰 패킷을 처리하도록 하는 다른 작업을 수행할 때 발생할 수 있는 `var/log/exception.log`의 데이터베이스 연결 오류에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스, 모든 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

[!DNL MySQL] 클라이언트 또는 [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) 서버가 [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet)바이트보다 큰 패킷을 받으면 [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) 오류가 발생하고(`exception.log`에서 볼 수 있음) 연결을 닫습니다. 일부 클라이언트의 경우 통신 패킷이 너무 큰 경우 [!DNL MySQL] 서버에 대한 *연결 끊김* 오류가 발생할 수 있습니다.

<u>재현 단계</u>

다양한 작업에서 이 문제를 발생시킬 수 있습니다. 여기에는 많은 수의 제품을 Adobe Commerce으로 가져오려고 시도하거나 너무 많은 데이터를 다시 보내는 트랜잭션 쿼리가 포함될 수 있습니다. 그 결과 `var/log/exception.log`에서 데이터베이스 연결 오류가 발생하고 제품을 제대로 가져오지 못하는 등의 다른 문제가 발생합니다.

## 원인

[!DNL MySQL] `max_allowed_packets` 설정의 기본값인 16MB가 필요에 맞게 충분히 크지 않습니다.

## 솔루션

1. 개별 행이 현재 `max_allowed_packet` 제한을 초과하는 쿼리를 식별합니다. 이러한 쿼리는 반환되는 데이터의 양을 줄이기 위해 다시 작성해야 합니다. 이 작업은 `SELECT` 문에 더 적은 수의 열이 있거나 테이블 디자인의 일부로 다양한 열에 대해 더 작은 데이터 형식을 선택하여 수행할 수 있습니다. New Relic 계정이 있는 경우 [New Relic APM 오류 페이지](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors), [New Relic APM 데이터베이스 페이지](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) 및 [New Relic 로그](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management)를 사용하여 관련 쿼리를 검색하십시오.
1. 빠른 수정을 위해 [티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)할 때 `max_allowed_packet` 크기를 늘리도록 일시적으로 요청할 수 있지만, 값이 너무 크면 네트워크 정체가 발생하여 복제 오류가 발생할 수 있으므로 이는 고객 엔지니어링 팀의 판단에 따른 것입니다.
1. 가장 좋은 방법은 일부 대용량 데이터베이스 테이블에 대해 CLI에서 다음 명령을 실행하는 것입니다.

   ```
   show table status like [table name to match]
   ```

   이러한 테이블에서 실행 중인 쿼리를 평가하여 권장 `max_allowed_packet` 크기인 16MB를 초과하는지 확인하십시오. 1단계에서 동일한 프로세스를 따라 이러한 쿼리에서 반환되는 데이터를 줄입니다.

## 관련 읽기

* 개발자 설명서에서 [온-프레미스 설치 개요](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/overview).
* [데이터베이스를 업로드하면 지원 기술 자료에서  [!DNL MySQL]](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql)에 대한 연결이 끊어집니다.
* 지원 기술 자료의 [클라우드 인프라에서 Adobe Commerce에 대한 데이터베이스 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=ko).
* 지원 기술 자료에서 [데이터베이스 성능 문제를 해결하는 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=ko).
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
