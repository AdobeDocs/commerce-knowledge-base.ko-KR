---
title: 클라우드 인프라의 Adobe Commerce에서 데이터베이스 덤프 만들기
description: 이 문서에서는 Adobe Commerce on cloud infrastructure에서 데이터베이스(DB) 덤프를 생성하는 가능한(및 권장되는) 방법에 대해 설명합니다.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에서 데이터베이스 덤프 만들기

이 문서에서는 Adobe Commerce on cloud infrastructure에서 데이터베이스(DB) 덤프를 생성하는 가능한(및 권장되는) 방법에 대해 설명합니다.

하나의 변형(옵션)만 사용하여 DB를 덤프하면 됩니다. 이러한 옵션은 모든 환경 유형(통합, 스테이징, 프로덕션) 및 모든 계획(Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 및 Adobe Commerce on cloud infrastructure Pro 계획 아키텍처)에 적용됩니다.

## 전제 조건: SSH를 환경에

이 문서에 설명된 변형을 사용하여 클라우드 인프라의 Adobe Commerce에 있는 DB를 덤프하려면 먼저 [SSH를 환경에 연결](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)해야 합니다.

>[!WARNING]
>
>옵션 1을 선택하든 옵션 2를 선택하든 데이터베이스 보조 노드에 대해 사용량이 적은 시간 동안 명령을 실행하십시오.

## 옵션 1: db-dump(**ece-tools; 권장**)

[ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) 명령을 사용하여 DB를 덤프할 수 있습니다.

```php
vendor/bin/ece-tools db-dump
```

권장되는 가장 안전한 옵션입니다.

Commerce on Cloud Infrastructure 안내서의 [데이터베이스 덤프(ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html)를 참조하십시오.

## 옵션 2: mariadb-dump(또는 이전 버전의 경우 mysqldump)

+++<b>최신 MariaDB 버전(11.x 이상)의 경우</b>

MariaDB 11.0.1부터 `mysqldump` symlink는 더 이상 사용되지 않습니다. 대신 `mariadb-dump`을(를) 사용하는 것이 좋습니다.

자세한 내용은 [mariadb-dump 클라이언트 유틸리티](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump)를 참조하세요.

+++

+++<b>이전 MariaDB 버전의 경우</b> 

`mariadb-dump`을(를) 사용할 수 없는 이전 MariaDB 버전인 경우 기본 MySQL `mysqldump` 명령을 사용하여 DB를 덤프할 수 있습니다.

>[!WARNING]
>
>데이터베이스 클러스터에 대해 이 명령을 실행하지 마십시오. 클러스터는 기본 데이터베이스에 대해 실행되는지 보조 데이터베이스에 대해 실행되는지 여부를 구분하지 않습니다. 클러스터가 기본 데이터베이스에 대해 이 명령을 실행하는 경우 덤프가 완료될 때까지 데이터베이스가 쓰기를 실행할 수 없으며 성능 및 사이트 안정성에 영향을 미칠 수 있습니다.

전체 명령은 다음과 같습니다.

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

`mysqldump` 명령을 실행하여 만들어지고 `\tmp`에 저장된 데이터베이스 백업을 이 위치에서 이동해야 합니다. `\tmp`에서 저장 공간을 차지해서는 안 됩니다(문제가 발생할 수 있음).

+++

DB 자격 증명(호스트, 사용자 이름 및 암호)을 얻으려면 `MAGENTO_CLOUD_RELATIONSHIPS` 환경 변수를 호출할 수 있습니다.

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**관련 설명서:**

* 공식 MySQL 설명서의 [mysqldump - 데이터베이스 백업 프로그램](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html).
* Commerce on Cloud Infrastructure 안내서의 [클라우드별 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)&#x200B;(`MAGENTO_CLOUD_RELATIONSHIPS` 참조).
