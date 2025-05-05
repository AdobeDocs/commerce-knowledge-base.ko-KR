---
title: 구성 요소 종속성 준비 확인 문제
description: 이 문서에서는 구성 요소 종속성 충돌에 대한 해결 방법을 제공합니다.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 구성 요소 종속성 준비 확인 문제

이 문서에서는 구성 요소 종속성 충돌에 대한 해결 방법을 제공합니다.

## 구성 요소 종속성 충돌 해결 {#resolve-component-dependency-conflicts}

표시된 순서대로 다음 솔루션을 사용해 보십시오.

1. [종속성 충돌](#trouble-depend-conflict)
1. [파일 시스템 권한 문제](#trouble-depend-permission)
1. [구성 요소 종속성 확인 상태는 변경되지 않습니다](#trouble-depend-state)

### 종속성 충돌 {#trouble-depend-conflict}

작성기에서 설치 또는 업데이트할 구성 요소를 결정할 수 없는 경우 *충돌하는 구성 요소 종속성을 찾았습니다* 메시지가 표시됩니다. 구성 요소 종속성 문제를 해결하려면 Composer의 작동 방식을 철저히 이해하는 기술 인력이어야 합니다.

다음은 실패 메시지의 예입니다.

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>표시되는 메시지는 다를 수 있습니다.

지원 기술 자료에서 [솔루션에 대한 구성 요소 종속성 충돌](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md)을(를) 참조하십시오.

## 파일 시스템 권한 문제 {#trouble-depend-permission}

Adobe Commerce 파일 시스템 소유자에게 Adobe Commerce 파일 시스템의 디렉터리에 대한 쓰기 권한이 없는 경우 다음과 유사한 메시지가 표시됩니다.

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

개발자 설명서의 [소유권 및 권한 개요](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) 문서에 설명된 대로 파일 시스템 권한을 설정해야 합니다.

## 구성 요소 종속성 확인 상태는 변경되지 않습니다 {#trouble-depend-state}

문제를 해결한 후에도 구성 요소 종속성 확인의 상태가 변경되지 않는 경우가 있습니다. 이 경우 `<magento_root>/var/.update_cronjob_status` 및 `<magento_root>/var/.setup_cronjob_status` 파일을 삭제하거나 이름을 바꾸고 구성 요소 관리자를 다시 실행할 수 있습니다.

이러한 파일의 이름을 바꾸거나 파일을 제거하면 구성 요소 관리자가 검사를 다시 실행해야 합니다.
