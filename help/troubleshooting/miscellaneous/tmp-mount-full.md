---
title: Adobe Commerce에 대한 /tmp 마운트 가득 참 문제 해결
description: 이 문서에서는 "/tmp" 마운트가 꽉 차고, 사이트가 다운되었을 수 있으며, 노드에 SSH를 수행할 수 없는 경우에 대한 해결 방법을 제공합니다.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Adobe Commerce에 대한 /tmp 마운트 가득 참 문제 해결

이 문서에서는 `/tmp` 마운트가 꽉 찼거나 사이트가 다운되었을 수 있으며 노드에 SSH를 사용할 수 없는 경우 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## 문제

`/tmp` 마운트가 꽉 차면 다음 오류를 비롯하여 다양한 증상이 나타날 수 있습니다.

* *SQLSTATE[HY000]: 일반 오류: 파일을 쓰는 동안 오류 발생*
* *오류 코드: 28*
* *장치(28)에 남은 공간이 없습니다*
* *오류 session_start(): 실패: 장치에 남아 있는 공간이 없습니다*
* *오류 1(HY000): &#39;/tmp/* 파일을 만들거나 쓸 수 없습니다.
* *SQL 오류: 3, SQLState: HY000*
* *일반 오류: 1021 디스크가 꽉 찼습니다(/tmp)*
* *SSH를 통해 노드에 액세스할 수 없음:*
  *bash: here-document에 대한 임시 파일을 만들 수 없음: 장치에 남아 있는 공간이 없음*
* *오류 번호: 28 &quot;장치에 남은 공간이 없습니다.&quot;*
* *mysqld: &#39;/tmp&#39;*&#x200B;을(를) 쓰는 동안 디스크가 꽉 찼습니다.
* *[오류] mysqld: 디스크가 꽉 찼습니다(/tmp)*
* *SQLSTATE[HY000]: 일반 오류: 1에서 &#39;/tmp/&#39; 파일을 만들거나 쓸 수 없습니다.*
* *SQLSTATE[HY000]: 일반 오류: &#39;/tmp/&#39; 파일을 열 때 23 리소스가 부족합니다.*
* *오류 코드: 24 &quot;열려 있는 파일이 너무 많습니다&quot;*
* *오류: 23: 파일을 열 때 리소스가 부족합니다*


<u>재현 단계:</u>

`/tmp` 마운트가 얼마나 찼는지 확인하려면 CLI에서 `/tmp`(으)로 전환하고 다음 명령을 실행하십시오.

```bash
 df -h
```

<u>예상 결과</u>:

80% 미만.

<u>실제 결과</u>:

약 100%.

## 원인

`/tmp` 마운트에 파일이 너무 많습니다. 원인은 다음과 같습니다.

* 대형 및/또는 너무 많은 임시 테이블을 생성하는 잘못된 SQL 쿼리입니다.
* 서비스가 `/tmp` 디렉터리에 쓰는 중입니다.
* `/tmp` 디렉터리에 데이터베이스 백업/덤프가 남아 있습니다.

## 솔루션

한 번에 공간을 확보하기 위해 수행할 수 있는 작업이 있으며, `\tmp`이(가) 꽉 차지 않도록 하는 모범 사례가 있습니다.

### inodes 확인 및 해제

사용 가능한 인사이트가 충분한지 확인합니다. 이렇게 하려면 다음 명령을 실행합니다.

```bash
df -i
```

출력은 다음과 비슷합니다.

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Use%가 70% 미만인지 확인합니다. Inode는 파일과 관련이 있습니다. 파티션에서 파일을 제거하면 inodes를 사용할 수 있습니다.

### 저장소 공간 확인 및 사용 가능

`/tmp`에 파일을 저장하는 서비스가 여러 개 있습니다.

#### MySQL 공간 확인 및 사용 가능

[MySQL 디스크 공간이 클라우드 인프라의 Adobe Commerce에 부족함 > 지원 기술 자료에서 저장소 공간 확인 및 사용 중지](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free)의 지침을 따르십시오.

#### Elasticsearch 덤프 확인

>[!WARNING]
>
>헤드덤프에는 문제 조사에 유용할 수 있는 로깅 정보가 포함되어 있습니다. 최소 10일 동안 별도의 위치에 저장하는 것이 좋습니다.

시스템 셸을 사용하여 헤더(`*.hprof`)를 제거합니다.

```bash
find /tmp/*.hprof -type f -delete
```

다른 사용자가 만든 파일을 삭제할 권한이 없지만(이 경우, Elasticsearch) 파일이 큰 경우 [지원 티켓을 만들기](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 처리하십시오.

#### 데이터베이스 덤프/백업 확인

>[!WARNING]
>
>데이터베이스 백업은 일반적으로 특정 용도로 만들어집니다. 파일이 계속 필요한지 확실하지 않은 경우 파일을 삭제하는 대신 별도의 위치로 이동하는 것이 좋습니다.

`/tmp`에서 `.sql` 또는 `.sql.gz` 파일을 확인하고 정리하십시오. 이러한 데이터는 백업 중에 또는 `mysqldump` 도구를 사용하여 데이터베이스 덤프를 수동으로 만들 때 ece-tools에 의해 만들어졌을 수 있습니다.

### 우수 사례

`/tmp`이(가) 가득 찬 문제가 발생하지 않도록 하려면 다음 권장 사항을 따르십시오.

* 검색에 MySQL을 사용하지 마십시오. Elasticsearch을 사용하면 대부분의 무거운 임시 테이블을 만들 필요가 없습니다. 개발자 설명서에서 [Elasticsearch을 사용하도록 Adobe Commerce 구성](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine)을 참조하십시오.
* 인덱스가 없는 열에서 `SELECT` 쿼리를 실행하지 마십시오. 이렇게 하면 많은 양의 임시 디스크 공간이 사용되기 때문입니다. 색인을 추가할 수도 있습니다.
* CLI에서 다음 명령을 실행하여 `/tmp`을(를) 정리할 cron을 만드십시오.

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## 관련 읽기

지원 기술 자료의 [클라우드 인프라의 Adobe Commerce에서 MySQL 디스크 공간이 부족합니다](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).
