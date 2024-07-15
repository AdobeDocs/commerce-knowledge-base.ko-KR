---
title: PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 도중 오류 발생
description: 이 문서에서는 PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 중에 발생하는 오류에 대한 해결책을 제공합니다.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 도중 오류 발생

이 문서에서는 PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 중에 발생하는 오류에 대한 해결책을 제공합니다.

## 영향을 받는 제품 및 버전

* cloud infrastructure 2.4.4 이상 버전의 Adobe Commerce

* 확장 또는 기술(Fastly, New Relic 등) 버전 PHP 8.1

## 문제

PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 중에 다음 오류가 발생합니다.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## 원인

PHP 8.1에는 이미 JSON 지원이 포함되어 있으므로 확장을 별도로 설치할 필요가 없습니다.

## 솔루션

`.magento.app.yaml`의 **런타임** > **확장** 섹션에서 JSON을 제거하고 다시 배포합니다.

## 관련 읽기

개발자 설명서에서 [PHP 응용 프로그램](https://devdocs.magento.com/cloud/project/magento-app-php-application.html).
