---
title: '클라우드에서 백업(스냅샷): FAQ'
description: 이 문서에서는 클라우드 인프라의 Adobe Commerce에서 스냅샷을 사용하여 환경을 백업하는 데 필요한 필수 사항을 다룹니다.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 3df2d07bb5765fb0ddcb4417b7c4e4ae33ef2d42
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 0%

---

# 클라우드에서 백업(스냅샷): FAQ

이 문서에서는 클라우드 인프라의 Adobe Commerce에서 스냅샷을 사용하여 환경을 백업하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.x
* 아키텍처 계획: Starter, Pro Legacy, Pro

## 환경 스냅샷, Pro 플랜

### 스테이징 및 프로덕션 환경

* Pro 플랜의 스테이징 및 프로덕션 환경에서는 수동 스냅샷을 사용할 수 없습니다.
* 사이트의 라이브 상태에 관계없이 **자동 스냅숏이 만들어집니다**(아직 시작되지 않은 사이트에 대해서도 스냅숏이 만들어집니다). 자동 백업은 별도의 시스템에 저장되므로 공개적으로 액세스할 수 없습니다.
티켓의 날짜, 시간 및 시간대를 제공하는 특정 백업에서 복원하거나 특수 백업을 요청하려면 [Adobe Commerce 지원 티켓을 제출](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)할 수 있습니다. 인프라 팀이 스냅샷을 제공하면 원래 타임스탬프가 찍혔는지 확인하려면 스냅샷이 배치된 위치에서 다음 명령을 실행합니다.

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  출력 예:

  <strong>2025-01-13 08:42:17.123000+00:00</strong>


* 지원에서 필요 시 수동 스냅샷을 생성하지 않습니다. 또한 지원에서 데이터베이스의 롤백 또는 복원은 자동으로 수행되지 않습니다. 스냅샷을 검색하지만 데이터베이스를 직접 복원해야 합니다.
* 사이트의 라이브 상태에 관계없이 **자동 스냅숏이 만들어집니다**(아직 시작되지 않은 사이트에 대해서도 스냅숏이 만들어집니다). 자동 백업은 별도의 시스템에 저장되며 일반인이 액세스할 수 없습니다.
티켓의 날짜, 시간 및 시간대를 제공하는 특정 백업에서 복원하거나 특수 백업을 요청하려면 [Adobe Commerce 지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md)할 수 있습니다. 지원에서 필요 시 수동 스냅샷을 생성하지 않습니다.
또한 지원에서 데이터베이스의 롤백 또는 복원은 자동으로 수행되지 않습니다. 스냅샷을 검색하지만 데이터베이스를 직접 복원해야 합니다.
* **암호화된 Amazon Web Services Elastic Block Store(AWS EBS) 스냅샷**&#x200B;을 사용하여 백업이 만들어집니다.
* 환경 스냅샷에는 전체 시스템(파일 시스템 및 데이터베이스)이 포함됩니다.
* 자동 스냅숏 **의 보존 시간이 다릅니다**. [일정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)을 따릅니다.

>[!NOTE]
>
>클라우드 콘솔은 항상 스테이징 및 프로덕션 환경에 [!UICONTROL No backup]을(를) 표시합니다. 통합 환경에서 백업만 가져올 수 있습니다. 줄임표 드롭다운 메뉴에서 **[!UICONTROL Backup]**&#x200B;을(를) 선택합니다.
>
>![cloud_console_backup.png](assets/cloud_console_backup.png)

### 통합(개발) 환경

* [통합 환경](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)이(가) **자동으로 백업되지 않습니다**. 하지만 스냅샷을 **수동으로** 만들 수 있습니다.
* 라이브 스토어가 아닌 스토어에서 통합 환경에 대한 수동 스냅샷을 생성할 수 있습니다.
* 수동으로 트리거된 **여러 스냅숏**&#x200B;이 있을 수 있습니다.
* 수동으로 트리거된 스냅숏이 **7일** 동안 저장됩니다.

**개발자 설명서의 관련 문서:**

* [백업 및 재해 복구](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [스냅숏 만들기](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## 환경 스냅샷, 시작 계획

* 모든 유형의 환경(통합, 스테이징, 프로덕션) **이(가) 자동으로 백업되지 않습니다**. 스냅샷을 수동으로 만들 수 있습니다.
* 사이트의 라이브 상태&#x200B;**에 관계없이 수동 스냅숏**&#x200B;을(를) 만들 수 있습니다(아직 시작되지 않은 사이트에 대해서도 스냅숏을 만들 수 있음).
* 수동으로 트리거된 스냅숏이 **7일** 동안 저장됩니다.

## 환경 스냅샷 복원

지원되는 환경(통합, 스테이징, 프로의 프로덕션 계획 또는 프로의 통합 계획)에서 기존 스냅샷을 복원하려면 Commerce on Cloud Infrastructure Guide의 [Backup Management: Restore a manual backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)의 단계를 따릅니다.

## 데이터베이스(DB) 백업

DB 백업은 클라우드 스냅샷의 일부입니다.

스냅샷은 실행 중인 모든 서비스(예: **MySQL 데이터베이스**, Redis 등)의 모든 영구 데이터와 마운트된 볼륨에 저장된 파일을 포함하는 환경의 전체 백업입니다.

>[!NOTE]
>
>마운트된 볼륨에는 [쓰기 가능한 마운트](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts)만 포함/참조되며 `/app` 디렉터리의 일부만 포함됩니다. 다른 파일은 [빌드 및 배포 프로세스](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow)에서 생성/생성되며 Git 저장소에서 나머지 파일도 체크 아웃해야 합니다.

개발자 설명서에서 [스냅샷 및 백업 관리](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)를 참조하십시오.

특정 시점의 DB가 필요한 경우에만 Pro 프로덕션 및 스테이징에서 DB 스냅샷에 대한 [지원 요청](/help/help-center-guide/help-center/magento-help-center-user-guide.md)을 제출하십시오. 환경에 관계없이 DB의 현재 백업만 필요한 경우 기술 자료 문서 [Cloud에서 데이터베이스 덤프 생성](/help/how-to/general/create-database-dump-on-cloud.md)을(를) 참조하십시오.
