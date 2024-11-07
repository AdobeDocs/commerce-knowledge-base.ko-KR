---
title: 큰 MySQL 테이블 찾기
description: '''큰 테이블을 식별하려면 [데이터베이스에 연결](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) 문서에 설명된 대로 데이터베이스에 연결하고 다음 명령을 실행합니다. 여기서 ''project_id''는 클라우드 프로젝트 ID입니다.'''
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# 큰 MySQL 테이블 찾기

큰 테이블을 식별하려면 [데이터베이스에 연결](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) 문서에 설명된 대로 데이터베이스에 연결하고 다음 명령을 실행합니다. 여기서 `project_id`은(는) 클라우드 프로젝트 ID입니다.

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

전체 테이블 목록 및 크기가 표시됩니다. 목록을 살펴보고 크기가 커서 주의가 필요한 테이블을 확인할 수 있습니다.

## 관련 읽기

Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
