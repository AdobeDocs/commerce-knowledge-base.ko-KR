---
title: '[!DNL MySQL]개 테이블이 너무 큽니다.'
description: 이 문서에서는  [!DNL MySQL] 테이블이 1GB보다 클 때 문제가 되는 이유와 방지 방법에 대해 설명합니다.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL]개 테이블이 너무 큽니다.

이 문서에서는 [!DNL MySQL] 테이블의 크기가 1GB보다 클 때 문제가 되는 이유와 방지 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전:

* 클라우드 인프라의 Adobe Commerce 2.x.x
* Adobe Commerce 온-프레미스 2.x.x

## 문제

[!DNL MySQL] 테이블 크기는 사이트 성능에 직접적인 영향을 주지 않습니다. 그러나 테이블이 큰 경우 추가 데이터나 오래된 데이터가 있을 수 있으므로 이 테이블에 대한 삽입 작업이 자주 발생합니다. [!DNL MySQL]은(는) 읽기/쓰기 작업의 비율이 80%/20%인 데이터베이스용으로 설계되었습니다.  크기가 큰 테이블의 경우 1GB 이상의 [!DNL MySQL] 인덱스는 읽기 작업 시 성능을 향상시키도록 설계되었으므로 쓰기 작업 시 성능이 저하될 수 있습니다.

## 솔루션

성능 저하를 방지하려면 다음 옵션을 고려하십시오.

* CRON 작업을 만들어 큰 테이블을 정리합니다. 큰 테이블을 식별하는 방법에 대한 권장 사항을 보려면 지원 기술 자료에서 [큰 테이블 찾기 [!DNL MySQL] 테이블](/help/how-to/general/find-large-mysql-tables.md)를 참조하십시오.
* 1GB보다 큰 테이블의 경우 로그 쓰기에 최적화된 [!DNL MySQL] 엔진을 사용합니다. 예를 들어 아카이브 엔진이 있습니다.
* DB에 로그를 저장하지 않도록 기능을 업데이트합니다.

## 관련 읽기

* 지원 기술 자료에서 [크기가 너무 커서 엔터티 업데이트가 지연됨](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
