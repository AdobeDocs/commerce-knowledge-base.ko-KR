---
title: 일반적인 PHP 치명적인 오류 및 솔루션
description: 이 문서에서는 Adobe Commerce 로그와 문제가 표시된 솔루션을 통해 확인할 수 있는 몇 가지 일반적인 PHP 치명적 오류 빠른 예제를 나열합니다.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# 일반적인 PHP 치명적인 오류 및 솔루션

이 문서에서는 Adobe Commerce 로그와 문제가 표시된 솔루션을 통해 확인할 수 있는 몇 가지 일반적인 PHP 치명적 오류 빠른 예제를 나열합니다.

## 예

*의 PHP 치명적인 오류: &#39;*&#x200B;에서 최대 실행 시간(60초).... 초과했습니다.

## 솔루션

`php.ini` 파일에서 사용자 지정 `max_execution_time` 값을 설정하고 다시 배포하여 최대 실행 시간을 업데이트할 수 있습니다.

For example:

`max_execution_time = 120`

[php.ini 설정 사용자 지정](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) 문서를 참조하십시오.

## 예

*의 PHP 치명적인 오류: 792723456바이트를 소진하는 데 허용된 메모리 크기&#39;*(바이트 크기 예시).

## 솔루션

`php.ini` 설정을 사용자 지정합니다. 이 [php.ini 설정 사용자 지정](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) 문서를 참조하십시오.

## 예

*의 PHP 경고: 알 수 없음: 스트림을 열지 못했습니다. 해당 파일 또는 디렉터리가 없습니다.*

## 솔루션

`php.ini` 파일에서 Windows 스타일의 끝을 제거하지 마십시오. Windows에서는 캐리지 리턴(ASCII 0x0d 또는 \r)과 CR/LF라고도 하는 줄바꿈(\n)의 조합으로 줄 끝이 종료됩니다.

## 예

*의 PHP 치명적인 오류: PDOException이 발견되지 않았습니다. SQLSTATE\[HY000\] \[1040\]&#39;*&#x200B;에 연결이 너무 많습니다.

## 솔루션

MySQL 환경의 디스크 공간이 부족합니다. MySQL 환경에 더 많은 디스크 공간을 제공합니다.

## 예

*의 PHP 치명적인 오류: 발견되지 않은 TypeError: &#39;*&#39; Magento의 반환 값

## 솔루션

`<root>/tmp` 디렉터리가 꽉 찼을 수 있으므로 확인하세요. 꽉 차면 디렉터리에 더 많은 공간을 제공합니다. 이 경우 파일을 다른 디렉토리로 이동하거나 삭제할 수 있습니다.

## 관련 읽기

개발자 설명서에서:

* [PHP 설정 오류](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [필요한 PHP 설정](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Redis 확인](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Redis 구성](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [PHP 메모리 제한 오류](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [일반적인 문제에 대한 해결 방법 - 메모리 제한](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
