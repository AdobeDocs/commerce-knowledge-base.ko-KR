---
title: 백업 문제
description: 이 문서에서는 백업 생성 문제에 대해 가능한 해결 방법을 나열합니다.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 백업 문제

이 문서에서는 백업 생성 문제에 대해 가능한 해결 방법을 나열합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.3.x
* Magento Open Source 2.3.x

## 백업이 비활성화됨 {#backup-disabled}

Adobe Commerce 백업 기능이 시작되지 않거나 다음 메시지가 표시되는 경우 백업하기 전에 기능을 활성화해야 합니다.

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

다음 CLI 명령을 입력합니다.

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

백업에 대한 자세한 내용은 [파일 시스템, 미디어 및 데이터베이스 백업 및 롤백을 참조하십시오.](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/backup)

## 디스크 공간 부족 {#insufficient-disk-space-trouble-backup-space-}

디스크 공간이 부족하여 백업이 실패한 경우 일반적으로 일부 파일을 다른 저장 장치 또는 드라이브로 이동하여 디스크 공간을 확보해야 합니다. 그러나 다른 방법으로 문제를 해결할 수도 있습니다. 팁은 다음 리소스 중 하나를 참조하십시오.

* [디스크가 꽉 찼거나 디스크에 쓸 수 없는 것과 같은 Linux 및 Unix 시스템 하드 디스크 문제를 해결하기 위한 팁](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverfault: df에 디스크가 꽉 찼다고 되어 있지만 &#x200B;](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)은(는) 아닙니다.
* [unix.stackexchange.com: Linux에서 디스크 공간이 사라진 위치를 추적하시겠습니까?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## 운영 체제 오류 {#operating-system-error-trouble-backup-os-}

불행히도, 우리는 당신이 발생할 수있는 다양한 오류 때문에 특정 어떤 것을 추천하지 않습니다. 그러나 다음을 제안할 수 있습니다.

* 시스템 관리자에게 문의하십시오.
* [스택 Exchange](https://unix.stackexchange.com) 또는 [스택 오버플로](https://stackoverflow.com)와 같은 공개 포럼 검색
* [GitHub 문제](https://github.com/magento/magento2/issues)를 열면 도움을 드리겠습니다.

## 백업 실패 {#backup-fails-trouble-backup-all-}

백업이 실패하거나 모든 백업 테스트가 실패하면 [Adobe Commerce 파일 시스템 소유자](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)에게 Adobe Commerce 파일 시스템에 대한 충분한 권한과 소유권이 없을 수 있습니다. 예를 들어 다른 사용자가 파일을 소유하거나 파일이 읽기 전용일 수 있습니다.

파일 시스템 사용 권한과 `<magento_root>/var` 디렉터리 및 하위 디렉터리의 소유권에 특별히 주의하십시오. 자세한 내용은 [파일 시스템 권한 및 소유권 설정](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/file-system/configure-permissions)을 참조하십시오.
