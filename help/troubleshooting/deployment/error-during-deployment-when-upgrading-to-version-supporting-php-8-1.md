---
title: PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 도중 오류 발생
description: 이 문서에서는 PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 중에 발생하는 오류에 대한 해결책을 제공합니다.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%
---
# PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 도중 오류 발생

이 문서에서는 PHP 8.1을 지원하는 버전으로 업그레이드할 때 배포 중에 발생하는 오류에 대한 해결책을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.4. 및 나중에

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

개발자 설명서에서 [PHP 응용 프로그램](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/app/php-settings).
