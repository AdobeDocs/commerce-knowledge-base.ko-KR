---
title: Adobe Commerce 사이트 작동 중지 문제 해결사
description: 각 질문을 클릭하면 문제 해결사의 각 단계에서 답변 세부 사항이 표시됩니다.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Adobe Commerce 사이트 작동 중지 문제 해결사

각 질문을 클릭하면 문제 해결사의 각 단계에서 답변 세부 사항이 표시됩니다.

## 1단계 {#step-1}

+++**<https://status.adobe.com>에 문제가 있습니까?**

a. 예 - [Adobe Magento 상태](https://status.adobe.com/products/3350)를 확인했는데 문제가 표시되면 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 열어 추가 조사를 받으십시오.\
b. 아니요 - [Adobe Magento 상태](https://status.adobe.com/products/3350)를 확인했지만 문제가 표시되지 않은 경우 [단계 2](#step-2)로 진행합니다.

+++

## 2단계 {#step-2}

+++**http://status.fastly.com에 문제가 있습니까?**

a. 예 - [Fastly 상태](https://status.fastly.com/)를 확인했지만 문제가 표시되면 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 열어 추가 조사를 받으십시오.\
b. 아니요 - [Fastly 상태](https://status.fastly.com/)를 확인했지만 문제가 표시되지 않으면 [3단계](#step-3)로 진행합니다.

+++

## 3단계 {#step-3}

+++**웹 브라우저에서 웹 사이트를 확인하세요. 200(OK) 코드를 받았습니까?**

**Firefox**&#x200B;에서 오류 코드를 확인하려면: **메뉴 열기** 아이콘 > **웹 개발자** > **도구 전환** > **네트워크** 탭 > **모두** 필터 > **상태** 열을 클릭합니다. **Chrome**&#x200B;에서 오류 코드를 확인하려면: **메뉴 열기** 아이콘 > **추가 도구** > **개발자 도구** > **네트워크** 탭 > **모두** 필터 > **상태** 열을 클릭합니다.

a. 예 - 추가 조사를 위해 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 엽니다.\
b. 아니요 - [4단계](#step-4)로 진행합니다.

+++

## 4단계 {#step-4}

+++**어떤 웹 사이트 오류 코드를 받았습니까?**

a. 오류 코드 500 - `/var/log/platform/`의 로그를 확인합니다. 이 데이터에 문제가 없으면 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 열고 추가 조사를 위해 지금까지 보유한 문제 해결 정보를 포함할 수 있습니다.

b. 오류 코드 503 - `var/reports`의 로그를 확인합니다. 이 데이터에 문제가 없으면 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 열고 추가 조사를 위해 지금까지 보유한 문제 해결 정보를 포함할 수 있습니다.

c. 오류 코드 404 - 다음 쿼리를 실행합니다. `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` 쿼리가 테이블을 반환하는 경우 `update_exists` 값이 &quot;0&quot;이면 콘텐츠 스테이징 문제로 인해 모든 페이지, 상점 및 관리자에서 [오류 404](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) 문서를 참조하십시오. 다른 모든 경우에는 [5단계](#step-5)로 진행합니다.

d. 기타 오류 코드 - [5단계](#step-5)로 진행합니다.

+++

## 5단계 {#step-5}

+++**사이트가 느리거나 MySQL 또는 Redis에서 서버 부하, CPU 부하, 요청 처리 속도가 느리거나 중단이 있습니까?**

a. 예 - [CLI에서 DDOS 공격 확인](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md)의 단계를 진행합니다.\
b. 아니요 - `/var/log/exception.log` 및 `/var/log/deploy.log`의 로그를 확인하고 이 데이터에 문제가 없으면 [6단계](#step-6)로 진행하십시오.

+++

## 6단계 {#step-6}

+++**배포 오류 또는 배포 오류가 있습니까?**

a. 예 - [13단계](#step-13)로 진행합니다.\
b. 아니요 - [7단계](#step-7)로 진행합니다.

+++

## 7단계 {#step-7}

+++**Elasticsearch 오류가 있습니까?**

a. 예 - [Elasticsearch 확인](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)을 위한 단계를 진행합니다.\
b. 아니요 - [8단계](#step-8)로 진행합니다.

+++

## 8단계 {#step-8}

+++**MySQL 데이터베이스에 느린 쿼리가 있거나 잘못된 쿼리가 있습니까?**

a. 예 - [MySQL에서 느린 쿼리 및 프로세스 확인](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md)을 진행하고 이 [MySQL 쿼리 자습서](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html)에서 쿼리 구조를 확인합니다.\
b. 아니요 - [9](#step-9)단계로 진행합니다.

+++

## 9단계 {#step-9}

+++**정적 콘텐츠를 사용할 수 없습니까?**

a. 예 - [정적 콘텐츠 확인](https://support.magento.com/hc/en-us/articles/360031624091) 문서를 계속 참조하십시오.\
b. 아니요 - [10단계](#step-10)로 진행합니다.

+++

## 10단계 {#step-10}

+++**로그에 PHP에 치명적인 오류가 표시됩니까?**

a. 예 - [일반적인 PHP 치명적인 오류 및 해결 방법](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md)을 계속 확인하십시오.\
b. 아니요 - [11단계](#step-11)로 진행합니다.

+++

## 11단계 {#step-11}

+++**Redis 오류가 표시됩니까?**

a. 예 - [Redis가 실행 중인지 확인](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) 및 [Redis 문제 해결](https://redis.io/topics/problems)의 단계를 진행합니다.\
b. 아니요 - [12단계](#step-12)로 진행합니다.

+++

## 12단계 {#step-12}

+++**인덱서 오류가 표시됩니까?**

a. 예 - 색인이 다른 프로세스에 의해 잠긴 경우 [색인이 다른 프로세스에 의해 잠겼습니다](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md)를 참조하십시오. 다른 인덱서 오류가 있는 경우 추가 조사를 위해 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 여십시오.\
b. 아니요 - 추가 조사를 위해 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 엽니다.

+++

## 13단계 {#step-13}

+++**사용자 지정 모듈에 문제가 있습니까?**

a. 예 - [일반 사용자 지정 모듈 문제 해결 도움말](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md)을 계속 참조하십시오.\
b. 아니요 - [14단계](#step-14)로 진행합니다.

+++

## 14단계 {#step-14}

+++**후크 후 오류가 있습니까?**

a. 예 - 이 [MySQL 서버 오류 메시지 참조](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html)에서 MySQL 오류를 계속 확인합니다.\
b. 아니요 - [15단계](#step-15)로 진행합니다.

+++

## 15단계 {#step-15}

+++**작성기 패치에 문제가 있습니까?**

a. 예 - 컨설팅을 진행합니다. [패치를 적용하면 사이트가 다운됩니다](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. 아니요 - [16단계](#step-16)로 진행합니다.

+++

## 16단계 {#step-16}

+++**SQL 데이터베이스 오류가 있습니까?**

a. 예 - 이 [MySQL 서버 오류 메시지 참조](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html)에서 MySQL 오류를 계속 확인합니다.\
b. 아니요 - [17단계](#step-17)로 진행합니다.

+++

## 17단계 {#step-17}

+++**MySQL 데이터베이스 사용 불능 잠금 또는 응답하지 않는 MySQL 데이터베이스가 있습니까?**

a. 예 - 이 [MySQL의 교착 상태](/help/troubleshooting/database/deadlocks-in-mysql.md) 문서에서 MySQL 고정 상태를 계속 확인합니다.\
b. 아니요 - 추가 조사를 위해 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 엽니다.

+++

[1단계로 돌아가기](#step-1)

사이트 작동 중지 문제 해결 순서도를 보려면 [여기](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md)를 클릭하십시오.
