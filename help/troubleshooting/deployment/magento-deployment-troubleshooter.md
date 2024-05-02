---
title: Adobe Commerce 배포 문제 해결사
description: 배포 문제 해결사 도구를 사용하여 Adobe Commerce에서 배포가 중단되고 배포가 실패하는 문제를 해결할 수 있습니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 6177863da268f43cc30119cef6f718a04c46b3e6
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Adobe Commerce 배포 문제 해결사

배포 문제 해결사 도구를 사용하여 Adobe Commerce에서 배포가 중단되고 배포가 실패하는 문제를 해결할 수 있습니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.

## 1단계 - 서비스가 실행 중인지 확인 {#step-1}

+++**클라우드 인프라 서비스에 대한 Adobe Commerce의 지원 여부**

중단 배포 - Adobe Commerce 클라우드 인프라 서비스가 작동합니까? 확인 [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. 예 - 진행합니다. [2단계](#step-2).\
b. 아니요 - 유지 보수 또는 글로벌 가동 중단 예상 기간 및 업데이트를 확인합니다.

+++

## 2단계 - 다른 환경에서의 배포 확인 {#step-2}

+++**기존 환경에서 배포를 차단하는 다른 환경의 배포가 있습니까?**

진행 중인 활동 목록을 얻으려면 magento-cloud CLI를 사용하여 다음 명령을 실행합니다(한 개의 클라우드 프로젝트에만 추가된 경우).

```bash
magento-cloud --state=in_progress
```

진행 중인 활동 목록을 얻으려면 magento-cloud CLI를 사용하여 다음 명령을 실행합니다(여러 프로젝트에 추가된 경우).

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

기존 배포 활동에 대한 정보를 찾으려면 를 참조하십시오. [Cloud UI에 &quot;로그 스니핑&quot; 오류가 있는 경우 배포 로그 확인](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
(자세한 내용) 이 명령을 실행하여 해당 활동의 실행 로그를 가져올 수 있습니다.

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. 예 - 기존 환경에서 배포를 차단하는 다른 환경 문제를 해결합니다. 다음으로 진행 [3단계](#step-3).

b. 아니요 - 현재 환경 문제를 해결합니다. 다음으로 진행 [3단계](#step-3).

+++


## 3단계 - 모든 노드에서 SSH 확인 {#step-3}

+++**모든 노드에 SSH가 성공했습니까?**

a. 예 - 진행합니다. [4단계](#step-4).\
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 4단계 - 실행 중인 모든 서비스 확인 {#step-4}

+++**모든 서비스가 실행 중입니까?**

a. 예 - 진행합니다. [5단계](#step-5).\
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 5단계 - Bitbucket 실행 확인 {#step-5}

+++**Bitbucket을 사용하시겠습니까?**

a. 예 - 확인 [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. 아니요 - 에서 배포 로그 오류 확인 [로그 작성 및 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). 다음으로 진행 [6단계](#step-6).

+++

## 6단계 - 오류 코드 확인 {#step-6}

+++**오류 코드가 보고되었습니까?**

a. 예 - 진행합니다. [7단계](#step-7).\
b. 아니요 - 진행합니다. [8단계](#step-8).

+++

## 7단계 - 403 금지됨 오류 {#step-7}

+++**403 금지?**

a. 예 - 진행합니다. [16단계](#step-16).
b. 아니요 - 진행합니다. [9단계](#step-9).

+++

## 8단계 - 실행 중인 cron 작업 확인 {#step-8}

+++**현재 cron 작업이 실행 중입니까?** 분기에 ssh로 로그인하고 를 실행합니다. `ps aufxx |grep cron`.

a. 예 - 영향을 받는 분기(예: 기본)에서 ssh로 로그인합니다. 크론 작업을 죽이고 잠금을 해제합니다. 이로 인해 크론 작업이 종료되고 상태가 재설정됩니다. 실행 `php vendor/bin/ece-tools cron:kill` 그런 다음 `php vendor/bin/ece-tools cron:unlock`. 한 환경을 다른 환경으로 병합하는 중이었다면 두 환경에서 cron을 실행하는지 확인하십시오.\
b. 아니요 - 진행합니다. [17단계](#step-17).

+++

## 9단계 - 원격 클러스터에 응용 프로그램 배포 가능 오류 {#step-9}

+++**원격 클러스터에 응용 프로그램을 업로드할 수 없습니까?**

a. 예 - 진행합니다. [10단계](#step-10).\
b. 아니요 - 진행합니다. [11단계](#step-11).

+++

## 10단계 - 충분한 스토리지 확인 {#step-10}

+++**사용할 수 있는 창고죠?**

a. 예 - 계속 진행합니다. [11단계](#step-11).\
b. 아니요 - 검토 [디스크 공간 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## 11단계 - 디스크 공간 확인 {#step-11}

+++**_파일을 쓸 수 없습니다. 경고&#x200B;_?**

a. 예. [.magento.app.yaml에서 디스크 값 증가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) 다시 배포합니다. 그래도 안되면, [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. 아니요 - 계속 진행합니다. [12단계](#step-12).

+++

## 12단계 - 환경 재배포 실패 오류 {#step-12}

+++**환경 재배포 실패 오류**

a. 예 - 계속 진행합니다. [13단계](#step-13).\
b. 아니요 - 계속 진행합니다. [8단계](#step-8).

+++

## 13단계 - Elasticsearch 업그레이드 실패 확인 {#step-13}

+++**업그레이드 또는 배포 중인 Elasticsearch**

a. 예 - Elasticsearch이 업그레이드 단계를 실패했습니다. 을(를) 참조하십시오 [Elasticsearch 소프트웨어 호환성](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Elasticsearch 업그레이드가 여전히 작동하지 않으면 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **참고**: 클라우드 인프라의 Adobe Commerce에서는 인프라 팀에 48시간 영업시간 통지를 하지 않으면 서비스 업그레이드를 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 사항이 프로덕션에 적용되기 48시간 전에 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 필요한 서비스 업그레이드에 대한 세부 정보를 제공하고 업그레이드 프로세스를 시작할 시간을 명시합니다.\
b. 아니요 - 진행합니다. [14단계](#step-14).

+++

## 14단계 - 공간 제한 확인 {#step-14}

+++**파일 시스템이 inodes나 space에서 벗어났습니까?**

a. 예 - 다음을 참조하십시오. [디스크 공간 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. 아니요 - 진행합니다. [15단계](#step-15).

+++

## 15단계 - Elasticsearch 버전 오류 {#step-15}

+++**Elasticseach 버전에 대한 오류**

a. 예 - 진행합니다. [16단계](#step-16).\
b. 아니요 - 진행합니다. [21단계](#step-21).

+++

## 16단계 - 작성기 구성 확인 {#step-16}

+++**작성기 구성이 올바릅니까?**

a. 예 - 진행합니다. [10단계](#step-10).\
b. 아니요 - 검토 [작성기 문제 해결사 웹 페이지](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## 17단계 - 장기 실행 프로세스 확인 {#step-17}

+++**장기 실행 프로세스**

a. 예 - 장기 실행 프로세스를 식별한 다음 프로세스를 종료합니다.
1. 터미널에서 다음 명령을 실행합니다. `ps aufx`.
1. 장기 실행 프로세스의 PID를 찾습니다.
1. 다음을 사용하여 프로세스 종료 `kill -9 <PID>`.

재발생에 대해 배포를 모니터링합니다.

b. 아니요 - 진행합니다. [18단계](#step-18).

+++

## 18단계 - 후크 후 실패 확인 {#step-18}

+++**후크 후 실패/중단?**

a. 예 - 데이터베이스: [사용 가능한 디스크 공간](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), 손상, 불완전/손상된 테이블.\
b. 아니요 - 진행합니다. [19단계](#step-19).

+++

## 19단계 - 서드파티 확장이 배포를 차단하는지 확인 {#step-19}

+++**타사 확장을 사용하시겠습니까?**

a. 예 - 시도해 보십시오. [타사 확장 비활성화](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) 특히 오류에 확장 이름이 있는 경우 배포 실행(문제의 원인인지 확인)을 참조하십시오.\
b. 아니요 - 진행합니다. [20단계](#step-20).

+++

## 20단계 - 느린 쿼리 확인 {#step-20}

+++**오래 실행되는 쿼리**

[느린 쿼리 로그 및 MySQL 표시 프로세스 목록 확인](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. 예 - 오래 실행되는 쿼리를 모두 종료합니다. 리뷰 [MySQL 종료 구문](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 21단계 - Elasticsearch 버전 다운그레이드 {#step-21}

+++**Elasticsearch 버전을 다운그레이드하시겠습니까?**

a. 예 - 구성을 통해 수행할 수 없습니다. [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[1단계로 돌아가기](#step-1)
