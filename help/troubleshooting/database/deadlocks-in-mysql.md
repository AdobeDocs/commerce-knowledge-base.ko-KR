---
title: MySQL 교착 상태
description: 이 문서에서는 MySQL의 교착 상태에 대해 설명하여 사이트 가동 중단, 데이터베이스 가져오기 중단 또는 기타 Adobe Commerce 문제가 발생하는 경우 이를 식별하고 해결하는 데 도움이 됩니다.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MySQL 교착 상태

이 문서에서는 MySQL의 교착 상태에 대해 설명하여 사이트 가동 중단, 데이터베이스 가져오기 중단 또는 기타 Adobe Commerce 문제가 발생하는 경우 이를 식별하고 해결하는 데 도움이 됩니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.2.x 및 2.3.x
* 클라우드 인프라 2.2.x 및 2.3.x의 Adobe Commerce

## 문제

MySQL의 교착 상태는 둘 이상의 트랜잭션을 상호 보류하고 잠금을 요청할 때 발생합니다. 교착 상태가 항상 문제를 나타내지는 않지만 발생한 다른 MySQL 또는 Adobe Commerce 문제의 증상인 경우가 많습니다.

대개 응용 프로그램, 배포 또는 MySQL 로그에서 *&quot;교착 상태&quot;* 오류 또는 *&quot;교착 상태를 발견하여 잠금을 시도하는 경우 오류가 발생합니다. 트랜잭션을 다시 시작해 보십시오.&quot;*

## 원인

교착 상태는 여러 원인이 있을 수 있지만 가장 일반적인 원인은 DML/DDL 쿼리를 동시에 수행하면서 상호 작용(웹 사이트/프로세스/cron 작업/기타 사용자/MySQL 유지 관리/MySQL 가져오기)을 수행하는 경우입니다.

예를 들어 교착 상태와 데이터베이스 가져오기의 중단 원인이 될 수 있는 데이터베이스에 SQL 요청을 가져오지 않도록 먼저 사이트를 유지 관리 모드로 전환하여 중단된 MySQL 데이터베이스 가져오기를 방지하는 것이 좋습니다.

## 솔루션

1. 교착 상태 오류에 대한 응용 프로그램, 배포 또는 MySQL 로그를 확인합니다.
   * [Adobe Commerce 및 Magento Open Source 로그 위치](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html?lang=ko)
   * [클라우드 인프라의 Adobe Commerce 로그 위치](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=ko)
1. MySQL 프로세스 목록에서 `mysql -e 'show full processlist';` 명령을 사용하여 프로세스를 실행하고 있는지 확인하십시오.
1. 클라우드 인프라의 Adobe Commerce에서 MySQL 슬레이브가 활성화되어 있는지 확인합니다. 다음 문서를 참조하십시오. [변수 배포(MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#mysql_use_slave_connection).
1. 관련된 오류에 따라 솔루션이 저절로 표시되거나 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 열어야 하는 경우 유용한 로그 정보를 포함해야 할 수도 있습니다.

## 관련 읽기

* [교착 상태를 최소화하고 처리하는 방법](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [인덱서 최적화 - 인덱서 테이블 전환](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [대량 작업 - 메시지 사용](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>이 문서에는 일부 사람들이 인종차별주의자, 성차별주의자 또는 억압적이라고 생각할 수 있고 독자로 하여금 상처받거나, 트라우마를 받거나, 환영받지 못하게 만들 수 있는 업계 표준 소프트웨어 용어가 여전히 포함되어 있을 수 있다는 것을 알고 있습니다. Adobe이 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하고 있습니다.
