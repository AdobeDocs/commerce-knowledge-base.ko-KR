---
title: 구성 파일이 없거나 변경되었습니다.
description: Adobe Commerce에 대한 구성 파일이 누락 또는 변경되어 발생하는 문제를 해결하십시오.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# 구성 파일이 없거나 변경되었습니다.

이 문서에서는 구성 파일이 변경되거나 누락된 문제를 해결하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

구성 파일 `config.php` 및/또는 `env.php`이(가) 잘못 변경되었거나 없습니다.

## 솔루션

배포 프로세스는 각 구성 파일에 대한 백업 파일을 작성합니다.

* `app/etc/config.php.bak` — 시스템별 설정이 포함되어 있으며, 없는 경우 빌드하는 동안 자동으로 생성됩니다.
* `app/etc/env.php.bak` — 중요한 구성 데이터를 포함합니다.

ECE-tools `backup:restore` 명령을 사용하여 복원할 수 있습니다.

BAK 파일은 배포 프로세스의 결과입니다. 배포 후 구성 파일을 수동으로 변경하는 경우 변경 사항이 기존 BAK 파일에 반영되지 않습니다.

구성 파일을 복원하려면 다음을 수행하십시오.

1. [SSH](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh)을(를) 사용하여 원격 저장소에 로그인합니다.
1. 사용 가능한 백업 파일을 나열합니다.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. 구성 파일을 복원합니다.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   복원의 영향을 받는 기존 구성 파일 목록을 받게 됩니다.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. `--force` 옵션을 사용하여 모든 파일을 덮어씁니다.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. 선택적으로 특정 구성 파일을 복원할 수 있습니다.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
