---
title: 'SQL 쿼리: 비용 오류 설명'
description: 이 문서에서는 실패한 SQL 쿼리를 실행할 때 발생하는 EXPLAIN 비용 오류에 대한 솔루션을 제공합니다. PostgreSQL은 [EXPLAIN 명령](https://www.postgresql.org/docs/9.5/static/using-explain.html)이라는 것을 사용하여 SQL 쿼리의 비용을 결정합니다. 또한 이 명령을 사용하기 위해 SQL Report Builder을 빌드했습니다. 즉, 비용이 너무 크다고 간주되는 경우(쿼리 실행에 필요한 리소스 양이 임계값을 초과하는 경우) 쿼리가 실행되지 않고 EXPLAIN 메시지가 표시됩니다.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# SQL 쿼리: 비용 오류 설명

이 문서에서는 실패한 SQL 쿼리를 실행할 때 발생하는 EXPLAIN 비용 오류에 대한 솔루션을 제공합니다. PostgreSQL은 [EXPLAIN 명령](https://www.postgresql.org/docs/9.5/static/using-explain.html)이라는 명령을 사용하여 SQL 쿼리 비용을 결정합니다. 또한 이 명령을 사용하기 위해 SQL Report Builder을 빌드했습니다. 즉, 비용이 너무 크다고 간주되는 경우(쿼리 실행에 필요한 리소스 양이 임계값을 초과하는 경우) 쿼리가 실행되지 않고 EXPLAIN 메시지가 표시됩니다.

이러한 상황이 발생할 수 있는 몇 가지 이유가 있습니다. 다음은 받을 수 있는 메시지, 그 의미 및 문제 해결 방법입니다.

## 쿼리를 실행할 수 없습니다. \[xxx\]의 EXPLAIN 비용 값이 너무 커서 이 쿼리를 실행할 수 없습니다.

이 메시지가 표시되면 쿼리를 실행하는 데 비용이 너무 많이 들었음을 의미합니다. 이러한 상황에 대한 두 가지 권장 사항이 있습니다. 하나는 쿼리에서 ORDER BY 절을 제거하는 것입니다. 이는 비용이 많이 드는 작업입니다. 두 번째는 쿼리를 수정하기 위한 [최적화 문서](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html)의 팁을 따르는 것입니다.

## 쿼리를 실행할 수 없습니다. 이 쿼리는 제한 값인 10,000개를 초과하는 \[xxx\]개의 행을 반환합니다.

이 경우 가능한 결과 수가 SQL Report Builder에 대해 설정된 최대값을 초과합니다. 결과 수를 줄일 수 있는 몇 가지 방법이 있습니다.

* 쿼리에 필터를 추가해 보십시오.
* 가능하면 LIMIT를 사용합니다. 일부 테이블에는 많은 행이 있으며 결과를 제한하면 행 제한을 유지할 수 있습니다.

## EXPLAIN 응답을 구문 분석할 수 없습니다.

죄송합니다. 일반적으로 이 메시지는 문제가 발생했음을 의미합니다. 이 오류가 계속 발생하면 지원 센터에 문의하십시오.
