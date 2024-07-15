---
title: 설치하는 동안 예외 SessionHandler::read()
description: "이 문서에서는 Adobe Commerce 설치 중 **SessionHandler::read()** 오류에 대한 수정 사항을 제공합니다."
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# 설치하는 동안 예외 SessionHandler::read()

이 문서에서는 Adobe Commerce 설치 중 발생한 예외 **SessionHandler::read()** 오류에 대한 수정 사항을 제공합니다.

## 문제

Adobe Commerce을 설치하는 마지막 단계에서 다음 예외가 표시됩니다.

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>이 오류는 2015년 9월 28일 이전 코드 버전에서만 발생합니다. 9월 29일 이상의 코드를 설치하는 경우 이 오류가 발생하지 않습니다. Redis 구성 옵션에 대한 자세한 내용은 개발자 설명서에서 [Redis 구성](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)을 참조하십시오. 명령줄 설치 프로그램을 사용하여 Redis를 지정하는 방법에 대한 자세한 내용은 개발자 설명서에서 [설치 항목](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) 또는 [배포 구성 항목](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp)을 참조하십시오.

## 원인

이 문제는 `session.save_handler` PHP 매개 변수가 `files`이(가) 아닌 다른 세션 저장소(예: `redis`, `memcached` 등)로 설정된 경우에 발생합니다. 이 문제는 해결하기 위해 노력하고 있는 알려진 문제입니다.

## 솔루션:

* Adobe Commerce 코드를 업그레이드합니다. 개발자 설명서에서 [설치 안내서 > Adobe Commerce 소프트웨어 업데이트](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update)를 참조하십시오.
* 기존 코드에서 다음 해결 방법을 사용하십시오.

## `php.ini` 찾기 {#locate-php-ini}

다음 명령을 입력하여 `php.ini`을(를) 찾습니다.

```php
php -i | grep "Loaded Configuration File"
```

일반적인 위치는 다음과 같습니다.

* 우분투: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## 해결 방법 {#workaround}

1. `root` 권한이 있는 사용자는 텍스트 편집기에서 `php.ini`을(를) 엽니다.
1. `session.save_handler` 찾기
1. 다음 방법 중 하나로 설정합니다.
   * 주석을 달려면:

     ```php
     ;session.save_path = <path>
     ```

   * 파일 시스템 경로로 설정하려면 다음을 수행하십시오.

     ```php
     session.save_handler = files
     ```
