---
title: Cron 작업은 다른 그룹의 작업을 잠급니다.
description: 이 문서에서는 다른 cron 작업을 차단하는 특정 장기 cron 작업과 관련된 Adobe Commerce on cloud infrastructure 문제에 대한 솔루션을 제공합니다.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Cron 작업은 다른 그룹의 작업을 잠급니다.

이 문서에서는 다른 cron 작업을 차단하는 특정 장기 cron 작업과 관련된 Adobe Commerce on cloud infrastructure 문제에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure Pro 계획 아키텍처
* 2019년 5월 이전에 온보딩

## 문제

Adobe Commerce for cloud에서 복잡한 cron 작업(장기 실행 작업)이 있는 경우 실행을 위해 다른 작업을 잠글 수 있습니다. 예를 들어 인덱서의 작업은 무효화된 인덱서를 다시 인덱싱합니다. 완료하는 데 몇 시간이 걸릴 수 있으며 이메일 보내기, 사이트 맵 생성, 고객 알림 및 기타 사용자 지정 작업과 같은 다른 기본 cron 작업을 잠급니다.

<u>증상</u>:

cron 작업에 의해 실행되는 프로세스는 수행되지 않습니다. 예를 들어 제품 업데이트가 시간 동안 적용되지 않거나 고객 보고서에서 이메일을 받지 못한다고 보고합니다.

를 열 때 `cron_schedule` 데이터베이스 테이블에서 다음 작업을 볼 수 있습니다. `missed` 상태.

## 원인

이전에는 클라우드 환경에서 Jenkins 서버를 사용하여 cron 작업을 실행했습니다. Jenkins는 한 번에 하나의 작업 인스턴스만 실행합니다. 따라서 하나만 실행합니다. `bin/magento cron:run` 한 번에 하나씩 실행되는 프로세스입니다.

## 솔루션

1. 연락처 [Adobe Commerce 지원](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 자체 관리 cron을 활성화하십시오.
1. 편집 `.magento.app.yaml` git 분기에 있는 Adobe Commerce용 코드의 루트 디렉터리에 있는 파일입니다. 다음을 추가합니다.

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. 파일을 저장하고 스테이징 및 프로덕션 환경에 대한 업데이트를 푸시합니다(통합 환경의 경우와 동일한 방법).

>[!NOTE]
>
>이전 cron 구성을 여러 개로 전송할 필요가 없습니다. `cron:run` 새 cron 일정에 따라 표시됩니다. 일반 `cron:run` 위에서 설명한 대로 추가된 작업이면 충분합니다. 단, 사용자 정의 작업이 있는 경우 전송해야 합니다.

### 자체 관리 cron이 활성화되어 있는지 확인(Cloud Pro 스테이징 및 프로덕션에만 해당)

자체 관리 cron이 활성화되어 있는지 확인하려면 `crontab -l` 명령을 실행하고 결과를 관찰하십시오.

* 다음과 같은 작업을 볼 수 있는 경우 자체 관리 cron이 활성화됩니다.

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* 작업을 보고 를 가져올 수 없는 경우 자체 관리 cron이 활성화되지 않습니다. *&quot;이 프로그램을 사용할 수 없습니다.&quot;* 오류 메시지입니다.

>[!NOTE]
>
>자가 관리 cron이 활성화되었는지 확인하는 위에서 언급한 명령은 Starter 계획 및 개발/통합 환경에 적용되지 않습니다.

## 관련 읽기

* [cron 작업 설정](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html) 개발자 설명서에서
