---
title: 스테이징 또는 프로덕션에서 DB 스냅샷 복원
description: 이 문서에서는 클라우드 인프라의 Adobe Commerce에서 스테이징 또는 프로덕션에서 DB 스냅샷을 복원하는 방법을 보여 줍니다.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 3d75b53dd290731380b2da33e3c0a1f746b9275b
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# [!DNL Staging] 또는 [!DNL Production]에서 DB 스냅숏 복원

이 문서에서는 Cloud Pro 인프라의 Adobe Commerce에서 [!DNL Staging] 또는 [!DNL Production]에서 DB [!DNL snapshot]을(를) 복원하는 방법을 보여 줍니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

사용 사례에 가장 적합한 항목 선택:

* [메서드 1: 데이터베이스를 로컬 컴퓨터로 전송 [!DNL dump] 하고 가져오기](#meth2).
* [메서드 2:  [!DNL dump] 서버에서 직접 데이터베이스 가져오기](#meth3).

## 방법 1: [!DNL dump] 데이터베이스를 로컬 컴퓨터로 전송하고 가져옵니다. {#meth2}

단계는 다음과 같습니다.

1. [!DNL SFTP]을(를) 사용하여 데이터베이스 [!DNL snapshot]이(가) 배치된 위치로 이동합니다(일반적으로 [!DNL cluster]의 첫 번째 서버/노드(예: `/mnt/recovery-<recovery_id>`). 참고: 프로젝트가 Azure 기반, 즉 프로젝트 URL이 https://us-a1.magento.cloud/projects/&lt;cluster_id>와(과) 같은 경우 스냅샷은 대신 `/mnt/shared/<cluster ID>/all-databases.sql.gz` 또는 `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz`에 배치됩니다.

   참고: Azure 프로젝트의 스냅숏 형식은 다르며 가져올 수 없는 다른 데이터베이스를 포함합니다. 스냅샷을 가져오기 전에     덤프를 가져오기 전에 적절한 데이터베이스를 추출하기 위해 추가 단계를 수행해야 합니다.

   프로덕션의 경우:

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   스테이징의 경우:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: <cluster ID_stg>/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. [!DNL dump file] 데이터베이스(예: [!DNL Production]의 경우 `<cluster ID>.sql.gz`, [!DNL Staging]의 경우 `<cluster ID_stg>.sql.gz`)를 로컬 컴퓨터에 복사합니다.
1. 개발자 설명서에서 데이터베이스에 원격으로 연결하도록 [!DNL SSH tunnel]을(를) 설정했습니다. [[!DNL SSH] 및 [!DNL sFTP]: [!DNL SSH tunneling]](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn).
1. 데이터베이스에 연결합니다.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. 데이터베이스 [!DNL Drop]; [!DNL MariaDB] 프롬프트에서 다음을 입력하십시오.

   (대상: [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (대상: [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. [!DNL snapshot]을(를) 가져오려면 다음 명령을 입력하십시오.

   (대상: [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (대상: [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## 방법 2: 서버에서 직접 [!DNL dump] 데이터베이스를 가져옵니다. {#meth3}

단계는 다음과 같습니다.

1. 데이터베이스 [!DNL snapshot]이(가) 배치된 위치(일반적으로 [!DNL cluster]의 첫 번째 서버/노드)로 이동합니다(예: `/mnt/recovery-<recovery_id>`).
1. [!DNL drop]에 클라우드 데이터베이스를 다시 만들려면 먼저 데이터베이스에 연결하십시오.

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. 데이터베이스 [!DNL Drop]; [!DNL MariaDB] 프롬프트에서 다음을 입력하십시오.

   (대상: [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (대상: [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. 데이터베이스를 삭제한 후 데이터베이스를 다시 생성합니다.

   ```mysql
   create database [database_name];
   ```

1. [!DNL snapshot]을(를) 가져오려면 다음 명령을 입력하십시오.

   ([!DNL Production]에서 데이터베이스 백업을 가져오는 경우)

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   ([!DNL Staging]에서 데이터베이스 백업을 가져오는 경우)

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (다른 환경에서 데이터베이스 백업을 가져오는 경우)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (다른 환경에서 데이터베이스 백업을 가져오는 경우)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## 관련 읽기

개발자 설명서에서:

* [코드 가져오기: 데이터베이스를 가져옵니다](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] 및 [!DNL backup] 관리: [!DNL Dump] 데이터베이스](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [클라우드의 백업(스냅숏): FAQ](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/faq/backup-snapshot-on-cloud-faq)
