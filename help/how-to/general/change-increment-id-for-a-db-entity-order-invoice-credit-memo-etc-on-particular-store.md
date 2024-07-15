---
title: DB 엔티티에 대한 증분 ID 변경(주문, 송장, 대변 메모 등) 특정 스토어
description: 이 문서에서는 Adobe Commerce 데이터베이스(DB) 엔티티(주문, 송장, 대변 메모 등)에 대한 증분 ID를 변경하는 방법에 대해 설명합니다. 'ALTER TABLE' SQL 문을 사용하는 특정 Adobe Commerce 저장소.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# DB 엔티티에 대한 증분 ID 변경(주문, 송장, 대변 메모 등) 특정 스토어

이 문서에서는 Adobe Commerce 데이터베이스(DB) 엔티티(주문, 송장, 대변 메모 등)에 대한 증분 ID를 변경하는 방법에 대해 설명합니다. `ALTER TABLE` SQL 문을 사용하는 특정 Adobe Commerce 스토어에서.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스: 2.x.x
* 클라우드 인프라의 Adobe Commerce: 2.x.x
* MySQL: 모든 [지원되는 버전](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## 언제 증분 ID를 변경해야 합니까(대소문자)

다음과 같은 경우 새 DB 엔티티의 증분 ID를 변경해야 할 수 있습니다.

* 라이브 사이트에서 하드 백업 복원 후
* 일부 주문 레코드가 손실되었지만 해당 ID는 현재 판매자 계정의 결제 게이트웨이(예: PayPal)에서 이미 사용되고 있습니다. 이러한 경우 결제 게이트웨이는 동일한 ID를 가진 새 주문 처리를 중지하고 &quot;송장 ID 복제&quot; 오류를 반환합니다

>[!NOTE]
>
>또한 PayPal의 지급 입고 환경설정에서 송장 ID당 복수 지급을 허용하여 PayPal에 대한 지급 게이트웨이 문제를 해결할 수 있습니다. 지원 기술 자료에서 [PayPal 게이트웨이 거부 요청 - 중복 송장 문제](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md)를 참조하십시오.

## 전제 조건 단계

1. 새 증분 ID를 변경해야 하는 저장소 및 엔티티를 찾습니다.
1. MySQL DB에 [연결](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html)합니다. 클라우드 인프라의 Adobe Commerce의 경우 먼저 [환경에 SSH를 연결](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)해야 합니다.
1. 다음 질의를 사용하여 엔티티 시퀀스 테이블의 현재 auto\_increment 값을 확인합니다.

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### 예

*ID=1*&#x200B;인 스토어에서 주문에 대한 자동 증가를 확인하는 경우 테이블 이름은 다음과 같습니다.

```sql
'sequence_order_1'
```

`auto_increment` 열의 값이 *1234*&#x200B;인 경우 *ID=1*&#x200B;인 저장소에 배치된 다음 순서는 *ID \#100001234*&#x200B;입니다.

### 관련 설명서

* 개발자 설명서에서 [원격 MySQL 데이터베이스 연결을 설정](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html)합니다.

## 증분 ID를 변경하려면 엔티티 업데이트

다음 쿼리를 사용하여 엔티티를 업데이트합니다.

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>중요: 새 증가 값은 현재 증가값보다 커야 하며 작아야 합니다.

### 예

다음 쿼리를 실행한 후:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

스토어에서 *ID=1*&#x200B;인 다음 순서는 *ID \#100002000*&#x200B;입니다.

## 프로덕션 환경(클라우드)에 대한 추가 권장 단계

클라우드 인프라에서 Adobe Commerce의 프로덕션 환경에서 `ALTER TABLE` 쿼리를 실행하기 전에 다음 단계를 수행하는 것이 좋습니다.

* 스테이징 환경에서 증분 ID를 변경하는 전체 절차를 테스트합니다
* 실패 시 프로덕션 DB를 복원하기 위해 DB 백업을 [만들기](/help/how-to/general/create-database-dump-on-cloud.md)합니다.

## 관련 설명서

* 지원 기술 자료에서 [클라우드에 데이터베이스 덤프를 만듭니다](/help/how-to/general/create-database-dump-on-cloud.md).
* 개발자 설명서에서 [환경에 SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)합니다.
