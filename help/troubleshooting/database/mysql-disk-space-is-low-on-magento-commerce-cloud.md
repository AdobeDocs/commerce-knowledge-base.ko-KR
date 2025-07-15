---
title: 클라우드 인프라의 Adobe Commerce에서 [!DNL MySQL] 디스크 공간이 부족합니다.
description: 이 문서에서는 클라우드 인프라의 Adobe Commerce에서  [!DNL MySQL] 을(를) 위한 공간이 부족하거나 부족한 경우에 대한 해결 방법을 제공합니다. 증상으로는 사이트 중단, 고객이 장바구니에 제품을 추가할 수 없음, 데이터베이스에 연결할 수 없음, 데이터베이스에 원격으로 액세스할 수 없음, 노드에 SSH할 수 없음 등이 있습니다. 증상에는 또한 갈레라, 환경 동기화, PHP, 데이터베이스 및 배포 오류가 포함됩니다. [솔루션](https://support.magento.com/hc/en-us/articles/360058472572#solution)을 클릭하여 솔루션 섹션으로 바로 이동합니다.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 80343c834563e7550569d225979edfa6a997bcfc
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에서 [!DNL MySQL] 디스크 공간이 부족합니다.

이 문서에서는 클라우드 인프라의 Adobe Commerce에서 [!DNL MySQL]에 대한 공간이 부족하거나 부족한 경우에 대한 솔루션을 제공합니다. 증상으로는 사이트 중단, 고객이 장바구니에 제품을 추가할 수 없음, 데이터베이스에 연결할 수 없음, 데이터베이스에 원격으로 액세스할 수 없음, 노드에 SSH할 수 없음 등이 있습니다. 증상에는 또한 갈레라, 환경 동기화, PHP, 데이터베이스 및 배포 오류가 포함됩니다. [솔루션](https://support.magento.com/hc/en-us/articles/360058472572#solution)을 클릭하여 솔루션 섹션으로 바로 이동합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## 문제

데이터베이스가 너무 커집니다. 증상에는 데이터베이스 연결 손실, 데이터베이스 업로드 오류 및 기타 다양한 문제가 포함될 수 있습니다.

발생할 수 있는 오류:

갈레라:

* *SQLSTATE\[08S01\]: 통신 링크 실패: 1047 WSREP가 아직 응용 프로그램 사용을 위한 노드를 준비하지 않았습니다.*   *가져오기 오류:*
* *SQLSTATE\[HY000\]: 일반 오류: 1180 오류 5 &quot;입력/출력 오류&quot;*
* *SQLSTATE\[08S01\]: 통신 링크 실패: 1047 WSREP가 아직 응용 프로그램 사용을 위한 노드를 준비하지 않았습니다.*

환경 동기화 오류:

* *SQLSTATE: 일반 오류: 1180 커밋 중 오류 5 &quot;입력/출력 오류&quot;가 발생했습니다.*

PHP 오류:

* *php: PDO:\_\_construct(): [!DNL MySQL] 서버가 사라졌습니다.*
* *php 오류: PDO::\_\_construct(): 인사말 패킷을 읽는 동안 오류가 발생했습니다. PID=NNNN.*
* *오류 2013(HY000): &#39;초기 통신 패킷 읽기&#39; 시 [!DNL MySQL] 서버에 대한 연결이 끊어졌습니다. 시스템 오류: 0 &quot;내부 오류/검사(시스템 오류가 아님)&quot;.*

데이터베이스 오류:

* *오류\_코드: 1114*
* *InnoDB: FTS 보조 인덱스 테이블에 단어 노드를 쓰는 동안 오류가 발생했습니다(디스크 공간 부족).*
* *SQLSTATE\[HY000\]: 일반 오류: 2006 [!DNL MySQL] 서버가 사라졌습니다.*
* *\[ERROR\] 슬레이브 SQL: 쿼리에서 &#39;테이블 `<table\_name>`이(가) 꽉 찼습니다&#39; 오류가 발생했습니다.*
* *Unit mysql.service가 실패 상태로 들어갔습니다.*
* *오류: &#39;/var/run/mysqld/mysqld.sock&#39; 소켓을 통해 로컬 [!DNL MySQL] 서버에 연결할 수 없습니다(111 &quot;연결이 거부되었습니다&quot;)&#39;*
* *1205 잠금 대기 시간 초과; 트랜잭션을 다시 시작해 보십시오. 쿼리: INSERT INTO \`cron\_schedule\`(\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) 값(?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

배포 오류:

* *E: &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; 명령이 0이 아닌 종료 상태 255*&#x200B;를 반환했습니다.
* *E: &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 restart site-`<environment name>`g-nginx&#39;\]&#39; 명령이 0이 아닌 값으로 반환됨*
* *스키마를 업그레이드하는 중.. SQLSTATE\[HY000\]: 일반 오류: 1114 테이블 `<table\_name>`이(가) 가득 찼습니다*
* *SQLSTATE\[HY000\]: 일반 오류: 파일을 쓰는 동안 오류 발생 ./`<environment name>`/\#*
* *너비: `<filename>`(오류 코드: 28 &quot;장치에 남은 공간이 없음&quot;)* *인덱싱 오류(/tmp에 분리된 임시 .ibd 파일 포함):*
* *카탈로그 규칙 인덱서에서 예외가 발생했습니다. 그 이후에 임시 테이블이 정리되지 않고 현재 [!DNL MySQL] 마스터 노드*&#x200B;의 디스크를 채웁니다.

<u>재현 단계</u>:

CLI에서 다음 명령을 실행하여 `/data/mysql`(또는 [!DNL MySQL] 데이터 저장소가 구성된 곳)이 가득 찼는지 확인할 수 있는 방법 중 하나는 다음과 같습니다.

```bash
df -h
```

[!DNL MySQL] 디스크의 사용 가능한 메모리 중 10% 미만이 중단에 대한 기본 표시기입니다.

## 원인

충분한 Inodes, 사용 가능한 저장소 공간 및 임시 테이블을 생성하는 잘못된 쿼리와 같은 다양한 문제로 인해 `/data/mysql` 마운트가 꽉 찼을 수 있습니다.

## 솔루션

[!DNL MySQL]을(를) 원래 상태로 되돌리거나 중단되지 않도록 하는 즉각적인 단계를 수행할 수 있습니다. 큰 테이블을 플러시하여 공간을 확보하십시오.

그러나 장기 솔루션에는 더 많은 공간을 할당하고 [주문/송장/배송 보관](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) 기능을 사용하도록 설정하는 등 [데이터베이스 모범 사례](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive)를 따르는 것이 포함됩니다.

다음은 빠른 솔루션과 장기적인 솔루션에 대한 세부 사항입니다.

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

사용 % 가 70% 미만인지 확인합니다. Inode는 파일과 관련이 있습니다. 파티션에서 파일을 제거하면 inodes를 사용할 수 있습니다.

### 저장소 공간 확인 및 사용 가능

사용 가능한 저장소 공간을 확인합니다. 이를 위해 다음을 실행합니다.

```bash
df -k
```

출력은 다음과 비슷합니다.

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

사용 %가 70%를 초과하는 경우 일부 공간을 사용/추가하기 위해 조치를 취해야 합니다.

### 대용량 `ibtmp1`개 파일 확인

각 노드의 `ibtmp1`에서 큰 `/data/mysql` 파일을 확인하십시오. 이 파일은 임시 테이블의 테이블스페이스입니다. 임시 테이블을 생성하는 잘못된 쿼리가 있는 경우 해당 쿼리는 `ibtmp1` 파일에 포함되어 있습니다. 이 파일은 데이터베이스가 다시 시작될 때만 제거됩니다. 사용 가능한 모든 공간을 사용하는 경우 데이터베이스를 다시 시작해야 합니다. 잘못된 쿼리가 있는 경우 다시 생성됩니다.

### 큰 테이블 초기화

>[!WARNING]
>
>조작을 수행하기 전에 데이터베이스 백업을 만들고 사이트 로드가 많은 기간 동안에는 이를 피하는 것이 좋습니다. 개발자 설명서에서 [데이터베이스 덤프](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)를 참조하십시오.

큰 테이블이 있는지 확인하고 플러시할 수 있는 테이블이 있는지 확인합니다. 기본(소스) 노드에서 이 작업을 수행합니다.

예를 들어 보고서가 있는 표는 일반적으로 플러시할 수 있습니다. 큰 테이블을 찾는 방법에 대한 자세한 내용은 [크게 찾기 [!DNL MySQL] 테이블](/help/how-to/general/find-large-mysql-tables.md) 문서를 참조하십시오.

대용량 보고서 테이블이 없는 경우 Adobe Commerce 응용 프로그램을 정상 상태로 되돌리기 위해 `_index` 테이블을 플러시하는 것이 좋습니다. `index_price`개 테이블이 가장 적합한 후보입니다. 예를 들어 `catalog_category_product_index_storeX`개의 테이블을 사용합니다. 여기서 X는 &quot;1&quot;부터 최대 저장소 개수까지의 값을 가질 수 있습니다. 이러한 테이블의 데이터를 복원하려면 색인을 다시 지정해야 하며 큰 카탈로그의 경우 이 색인 재지정에 많은 시간이 걸릴 수 있습니다.

플러시하고 나면 wsrep 동기화가 완료될 때까지 기다립니다. 이제 백업을 만들고 더 많은 공간을 할당/구매하고 [주문/송장/배송 보관](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive) 기능을 활성화하는 등 더 중요한 단계를 수행하여 공간을 추가할 수 있습니다.

### 이진 로깅 설정 확인

[!DNL MySQL] 서버 이진 로깅 설정을 확인합니다. `log_bin` 및 `log_bin_index`. 이 설정을 사용하면 로그 파일이 커질 수 있습니다. [지원 티켓을 만듭니다](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 큰 이진 로그 파일을 제거하도록 요청합니다. 또한 로그가 주기적으로 삭제되고 공간이 너무 많이 차지하지 않도록 바이너리 로깅이 올바르게 구성되어 있는지 확인하는 요청입니다.

[!DNL MySQL] 서버 설정에 대한 액세스 권한이 없는 경우 지원을 요청하여 확인하세요.

### 사용되지 않는 할당된 디스크 공간 재확보

1. SSH를 노드 1에 로그인한 다음 MySQL에 로그인합니다.

   ```sh
   mysql -h127.0.0.1 -p`php -r "echo (include('app/etc/env.php'))['db']['connection']['default']['password'];"` -u`whoami` `whoami`
   ```

   자세한 단계는 [Adobe Commerce 데이터베이스에 대한 쿼리 연결 및 실행](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/remote-db-connection-execute-queries)을 참조하세요.

1. 사용하지 않는 공간 확인:

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) AS size_MB, round((data_free)/1048576,2) AS Allocated_but_unused FROM information_schema.tables WHERE data_free > 1048576*10 ORDER BY data_free DESC;
   ```


   출력 예:

   | table_name | size_MB | 할당되었지만 사용되지 않음 |
   |----------------------|----------|--------------------------|
   | vertex_taxrequest | 28145.20 | 14943.00 |


   출력을 체크인하여 할당된 메모리가 있지만 사용되지 않는지 확인합니다. 이 문제는 데이터가 테이블 내에서 삭제되었지만 메모리가 여전히 해당 테이블에 할당된 경우 발생합니다.


1. 사이트를 유지 관리 모드로 전환하고 데이터베이스에서 발생하는 상호 작용이 없도록 cron 작업을 중지합니다. 단계는 [유지 관리 모드 사용 또는 사용 안 함](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) 및 [cron 작업 사용 안 함](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs)을 참조하세요.
1. 다음 명령을 사용하여 테이블을 다시 만들어 공간을 다시 확보합니다(예: 가장 많이 사용하지 않는 공간과 함께 위에 나열된 테이블 사용).

   ```sql
   ALTER TABLE vertex_taxrequest Engine = "INNODB";
   ```

1. **[!UICONTROL Allocated_but_unused]** 열 내에서 높은 값을 표시하는 각 테이블에 대해 할당되지 않은 공간을 확인하려면 다음 쿼리를 실행하십시오.

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) as size_MB, round((data_free)/1048576,2) as Allocated_but_unused FROM information_schema.tables WHERE 1 AND data_free > 1048576*10 ORDER BY 
   data_free DESC;
   ```


1. 이제 [유지 관리 모드를 사용하지 않도록 설정](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#enable-or-disable-maintenance-mode-1) 및 [크론 작업을 사용하도록 설정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs)합니다.


### 추가 공간 할당/구매

사용하지 않은 디스크 공간이 있는 경우 [!DNL MySQL]에 더 많은 디스크 공간을 할당하십시오. 사용 가능한 디스크 공간이 있는지 확인하는 방법은 [디스크 공간 제한 확인](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) 문서를 참조하십시오.

* Starter 계획, 모든 환경 및 Pro 계획 통합 환경의 경우 일부 사용하지 않는 디스크 공간이 있을 경우 디스크 공간을 할당할 수 있습니다. 자세한 내용은 [추가 공간 할당 [!DNL MySQL]](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md)을 참조하세요.
* Pro 계획 스테이징 및 프로덕션 환경의 경우 사용하지 않은 디스크 공간이 있는 경우 [지원에 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 더 많은 디스크 공간을 할당하십시오.

공간 제한에 도달했지만 여전히 공간 문제가 낮은 경우 더 많은 디스크 공간을 구입하는 것이 좋습니다. 자세한 내용은 Adobe 계정 팀에 문의하십시오.

## 관련 읽기

Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
