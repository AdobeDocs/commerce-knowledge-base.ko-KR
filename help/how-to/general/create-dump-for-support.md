---
title: 지원 에이전트가 요청할 때 "스크러빙된" 덤프를 만드는 방법
description: 이 문서에서는 Adobe Commerce 지원 에이전트에서 데이터베이스 및 코드 제공을 요청받은 경우 Adobe Commerce 관리자로부터 "스크러빙된" 덤프(백업)를 만드는 방법에 대한 정보를 제공합니다. 이 덤프는 프로세스 속도를 높이고 훨씬 작은 파일을 만들기 위해 미디어 파일을 제외합니다. 데이터베이스 백업을 수행할 때 모든 중요한 데이터가 해시됩니다.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: e07ade849a4105b5e499b5282d75cb1b5321b6ea
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 지원 에이전트가 요청할 때 &quot;스크러빙된&quot; 덤프를 만드는 방법


## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 방법) 2.3.x, 2.4.x.

## &quot;스크러빙된&quot; 덤프 만들기

책임자로부터 &quot;스크러빙된&quot; 덤프를 만듭니다.

1. Commerce 관리에서 **시스템** > **지원** > **데이터 수집기**&#x200B;로 이동합니다.
1. **새 백업**&#x200B;을 클릭합니다.
1. 몇 분 후에 **상태 새로 고침**&#x200B;을 클릭합니다(오래 걸릴 수 있으며, 완료될 때까지 5분마다 반복).
1. 생성된 덤프 파일을 `/var/support` 디렉터리에서 Adobe Commerce 루트 디렉터리로 재배치합니다.

그런 다음 지원 팀에 덤프 파일(저장소 주소 및 표시된 파일 이름)에 대한 직접 다운로드 링크를 제공할 수 있습니다.

관리자로부터 덤프를 만드는 데 문제가 있는 경우 개발자 설명서에서 [지원 유틸리티 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-spt-util.html)에 설명된 대로 CLI 명령을 사용하는 것이 좋습니다.

## 관련 읽기

* 지원 기술 자료에서 [클라우드 인프라의 Adobe Commerce에 대한 전체 데이터베이스 백업을 만듭니다](/help/how-to/general/create-database-dump-on-cloud.md).
