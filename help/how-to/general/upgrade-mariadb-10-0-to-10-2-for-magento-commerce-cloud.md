---
title: 클라우드에서 Adobe Commerce용 MariaDB 10.0을 10.2로 업그레이드
description: MariaDB 10.0 및 10.1은 EOL(수명 종료) 상태입니다. [지원이 2019년 3월 31일 및 2020년 10월 17일에 각각 종료됨](https://endoflife.date/mariadb). 이 문서에서는 클라우드 인프라에서 Adobe Commerce을 사용하기 위해 MariaDB를 10.0에서 10.2 또는 10.2에서 10.3 또는 10.4로 업그레이드하는 방법에 대해 설명합니다.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 클라우드에서 Adobe Commerce용 MariaDB 10.0을 10.2로 업그레이드

MariaDB 10.0 및 10.1은 EOL(수명 종료) 상태입니다. [지원이 2019년 3월 31일과 2020년 10월 17일에 각각 종료되었습니다](https://endoflife.date/mariadb). 이 문서에서는 클라우드 인프라에서 Adobe Commerce을 사용하기 위해 MariaDB를 10.0에서 10.2 또는 10.2에서 10.3 또는 10.4로 업그레이드하는 방법에 대해 설명합니다.

>[!NOTE]
>
>MariaDB 10.0은 서비스 종료(EOL)이며 현재 Adobe Commerce 버전에서 지원되지 않습니다. EOL 후 30일 이내에 EOL 버전을 사용하지 않는 것이 좋습니다.

## 영향을 받는 제품 및 버전

* MariaDB 10.2는 클라우드 인프라 2.3.x의 Adobe Commerce에 권장됩니다.
* 2.4.x에는 MariaDB 10.4가 권장됩니다. MariaDB 10.3은 클라우드 인프라 2.4.x의 Adobe Commerce과도 호환됩니다.

## 업그레이드 단계

MariaDB 10.0에서 10.2 또는 10.2에서 10.3 또는 10.4로 업그레이드하려면 다음 단계를 완료하십시오.

1. ECE-Tools DB 백업 명령을 사용하여 [DB 백업을 만듭니다](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump). 테이블/행을 업데이트하는 동안 문제가 발생할 경우 2단계와 3단계 전에 이 작업을 수행해야 합니다.
1. [모든 소형 테이블을 확인하고 동적 테이블로 변환](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html)합니다. 데이터베이스 업그레이드 중에 발생할 수 있는 데이터 손실을 방지하기 위해 필요합니다.
1. MYISAM 테이블을 확인합니다. [모든 MyISAM 테이블을 ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)(으)로 변환해야 합니다.
1. 데이터베이스 테이블 및 행을 준비한 후(앞의 두 단계) ECE-Tools DB 백업 명령을 사용하여 [DB 백업을 만듭니다](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
1. [지원 티켓을 엽니다](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) MariaDB 10.0에서 10.2 또는 10.2에서 10.3 또는 10.4로 업그레이드를 예약합니다. 티켓에는 DB를 업그레이드하려는 날짜 및 시간이 자세히 설명되어 있습니다. 지원 팀은 48시간 전에 통보해야 하며 상인 개발자 팀은 사용할 수 있어야 합니다. 업그레이드에 대한 시간 및 날짜가 합의되면 다음을 수행합니다.
   1. 사이트를 유지 관리 모드로 전환하고 크론과 같은 DB 활동을 중지합니다.
   1. ECE-Tools DB 백업 명령을 사용하여 [DB 백업을 만듭니다](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
   1. 백업을 완료했음을 지원 팀에 알립니다. 지원 티켓을 통해 이 작업을 수행합니다. 티켓을 보고 추적하는 단계를 보려면 지원 기술 자료에서 [Adobe Commerce 도움말 센터 사용 안내서: 티켓 추적](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)을 참조하십시오.
   1. Adobe Commerce 지원 팀이 MariaDB 업그레이드 프로세스를 시작합니다. 위의 모든 단계를 수행했으며 데이터베이스가 평균 크기인 경우 약 1시간 내에 완료할 수 있습니다. 더 큰 DB는 시간이 더 오래 걸립니다. 업그레이드가 완료되면 티켓을 통해 알려 드립니다.
1. 유지 관리 모드를 비활성화합니다. 개발자 설명서에서 [유지 관리 모드 활성화 또는 비활성화](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint)를 참조하십시오.

## 관련 읽기

Adobe Commerce 2.4.x에 대한 요구 사항에 대해 자세히 알아보려면 개발자 설명서에서 [Adobe Commerce 2.4 시스템 요구 사항 > 데이터베이스](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html#database)를 참조하십시오.
