---
title: Commerce 관리자의 잠긴(회색으로 표시됨) 필드
description: 이 문서에서는 Commerce 관리자의 필드를 수정할 수 없는 경우의 솔루션을 제공합니다.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Commerce 관리자의 잠긴(회색으로 표시됨) 필드

이 문서에서는 Commerce 관리에서 잠긴(회색으로 표시된) 필드를 수정할 수 없는 경우에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.3.x, 2.4.x
* 클라우드 인프라의 Adobe Commerce 2.3.x, 2.4.x

## 문제

구성의 변경 사항을 `app/etc/env.php` 또는 `app/etc/config.php`(으)로 저장하면 관리자의 설정을 수정할 수 없습니다.

<u>재현 단계</u>:

참고: 이 문제는 저장된 모든 구성에 영향을 줄 수 있는 예입니다.

1. 판매자가 터미널에서 `./vendor/bin/ece-tools config:dump` 명령을 사용하여 게재 방법 자격 증명을 저장합니다. 자격 증명이 `app/etc/env.php` 파일에 저장됩니다.
1. 그런 다음 머천트는 나중에 자격 증명을 변경하려고 시도합니다.

<u>예상 결과</u>:

판매자는 관리 필드 설정에서 값을 설정하고 저장할 수 있습니다.

<u>실제 결과</u>:

관리자의 필드가 잠겨 있거나 값을 변경할 수 있지만 관리자에 저장되지 않습니다.

## 원인

구성을 `env.php` 또는 `config.php`에 저장하면 관리자의 설정을 수정할 수 없습니다. 설정을 편집하려면 `env.php` 또는 `config.php`에서 구성을 제거해야 합니다.

## 솔루션

구성이 `app/etc/env.php` 또는 `app/etc/config.php`에 저장되지 않았는지 확인하십시오. 저장된 경우 다음 단계를 수행하십시오.

* `config.php` - 설정을 제거한 다음 다시 배포합니다.
* `env.php` - 서버에서 직접 수정하고 설정을 제거한 다음 `bin/magento app:config:import`을(를) 실행합니다.

## 관련 읽기

* 개발자 설명서에서 [구성을 내보내기](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/export-configuration).
* 개발자 설명서에서 [구성 값을 설정](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values)합니다.
* [클라우드 인프라의 Adobe Commerce: 구성 관리를 통해 배포 중단 시간을 줄입니다](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md).
