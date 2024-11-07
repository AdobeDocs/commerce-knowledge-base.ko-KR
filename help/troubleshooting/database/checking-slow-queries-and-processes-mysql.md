---
title: 느린 쿼리 및 프로세스 MySQL 확인
description: 이 문서에서는 판매자 사이트 및 해당 사이트가 표시하는 솔루션에 부정적인 영향을 줄 수 있는 몇 가지 일반적인 MySQL 문제(느린 쿼리, 프로세스 시간이 너무 오래 걸림)에 대해 설명합니다.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 느린 쿼리 및 프로세스 MySQL 확인

이 문서에서는 판매자 사이트 및 해당 사이트가 표시하는 솔루션에 부정적인 영향을 줄 수 있는 몇 가지 일반적인 MySQL 문제(느린 쿼리, 프로세스 시간이 너무 오래 걸림)에 대해 설명합니다.

## MySQL &quot;느린 쿼리&quot; 확인 중

### 설명

오버로드된 데이터베이스로 인해 잠재적으로 장애가 발생한 경우, 이러한 단계는 데이터베이스의 느린 쿼리 로그를 확인하는 데 도움이 됩니다.

### MySQL 명령줄(Adobe Commerce Cloud/온-프레미스/Magento Open Source)을 사용하여 쿼리 분석

1. MySQL 명령줄(Adobe Commerce 온-프레미스/Magento Open Source)이나 명령줄에서 클라우드 서버(클라우드 인프라의 Adobe Commerce)에 로그인합니다.
1. 느린 쿼리 로그에서 50초 이상의 쿼리를 검사합니다.

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. <https://www.unixtimestamp.com/>(또는 유사한 Unix 타임스탬프 변환기)로 이동하여 느린 쿼리가 실행된 시간의 타임스탬프를 삽입합니다.
1. 이 시간이 발생한 사이트 중단과 관련이 있는 경우 데이터베이스가 오버로드되어 발생할 수 있습니다. 해당 시간에 데이터베이스에 어떤 로드가 있는지 확인합니다. 이러한 로드의 예는 다음과 같습니다.

* Cron 프로세스
* 트래픽(보트 또는 사람)
* 스크립트 가져오기/내보내기
* 덤프 만들기


### [!DNL Percona Toolkit]을(를) 사용하여 쿼리 분석(Adobe Commerce Pro: 클라우드 아키텍처만)

Adobe Commerce 프로젝트가 Pro 아키텍처에 배포된 경우 [!DNL Percona Toolkit]을(를) 사용하여 쿼리를 분석할 수 있습니다.

1. MySQL 느린 쿼리 로그에 대해 `pt-query-digest --type=slowlog` 명령을 실행합니다.
   * 느린 쿼리 로그의 위치를 찾으려면 개발자 설명서에서 **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)**&#x200B;을(를) 참조하십시오.
   * [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 설명서를 참조하십시오.
1. 발견된 문제를 기반으로, 쿼리를 수정하는 단계를 수행하여 쿼리가 더 빨리 실행되도록 합니다.

## MySQL &quot;프로세스 목록&quot; 확인 중

### 설명

이렇게 하면 MySQL 서버가 활성 상태이고 중단된 쿼리가 없는지 식별하는 데 도움이 됩니다.

### 단계

1. MySQL 명령줄(Adobe Commerce 온-프레미스/Magento Open Source)이나 명령줄에서 클라우드 서버(클라우드 인프라의 Adobe Commerce)에 로그인합니다.
1. 아래 코드 블록을 사용하여 MySQL에 로그인합니다. 이렇게 하면 로그인 프로세스가 자동화됩니다.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. 오류가 반환되거나 응답하는 데 30초 이상 걸리는 경우 지원 센터에 문의하여 MySQL 서버를 확인해야 합니다.
1. 샘플 출력을 봅니다.

1. 다음은 일부 샘플 출력입니다.

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. 1800초 이상의 모든 시간에 대해 &quot;시간&quot; 열을 확인합니다. 이는 완료하는 데 시간이 너무 오래 걸릴 수 있는 프로세스를 나타냅니다. &quot;상태&quot; 열에 프로세스 상태를 확인합니다.
1. 쿼리를 검토하고 해당 시간 동안 실행되지 않을 것으로 예상되는 경우 쿼리를 종료할 수 있습니다. 장기 실행 쿼리를 예상할 수 있습니다.


## 관련 읽기

* dev.mysql.com의 [MySQL Show Processlist 구문](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html).
* dev.mysql.com의 [MySQL Kill 구문](https://dev.mysql.com/doc/refman/8.0/en/kill.html).
* 개발자 설명서에서 [보안, 성능 및 데이터 처리](https://developer.adobe.com/commerce/php/best-practices/extensions/security/).
* 개발자 설명서에서 [MySQL 도움말](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql)
