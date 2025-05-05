---
title: ECE-Tools 및 패치 업데이트 오류 Adobe Commerce cloud infrastructure 2.2.x., 2.3.x
description: 이 문서에서는 ECE-Tools, 패치 또는 기타 변경 사항에 업데이트를 배포하려고 할 때 "*스트림을 열지 못했습니다:*" 또는 "*해당 파일 또는 디렉터리가 없습니다*"와 같은 오류 메시지가 표시되는 문제에 대한 해결 방법을 제공합니다.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-Tools 및 패치 업데이트 오류 Adobe Commerce cloud infrastructure 2.2.x., 2.3.x

이 문서에서는 ECE-Tools, 패치 또는 기타 변경 사항에 업데이트를 배포하려고 할 때 &quot;*스트림 열기 실패:*&quot; 또는 &quot;*이러한 파일 또는 디렉터리 없음*&quot;을 포함하는 오류 메시지가 표시되는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce 2.2.x., 2.3.x

## 문제

ECE-Tools, 패치 또는 기타 변경 사항에 업데이트를 배포하려고 할 때 발생하는 오류: 클라우드 콘솔 및 `var/log/cloud.log`의 PHP 오류

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

예외 로그 오류:

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## 원인

`composer.json` 파일이 잘못 구성되었습니다.

## 솔루션

`composer.json` 파일에 설정이 없으면 일부 디렉터리가 Adobe Commerce 코드 베이스에서 복사되지 않습니다. 파일을 찾을 수 없기 때문에 패키지 및 업데이트/패치를 적용할 수 없습니다.

추가 섹션을 아래에 제공된 것과 일치하도록 변경하고 배포를 다시 시도하십시오.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## 관련 읽기

* 개발자 설명서에서 [업그레이드 및 패치](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/best-practices).
