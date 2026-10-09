---
title: 설치는 약 70%에서 중단됩니다.
description: 이 문서에서는 설치가 약 70%에서 중지되는 경우에 대한 수정 사항을 제공합니다.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# 설치는 약 70%에서 중단됩니다.

이 문서에서는 설치가 약 70%에서 중지되는 경우에 대한 수정 사항을 제공합니다.

## 문제

설치 마법사를 사용하여 설치하는 동안 프로세스는 약 70%에서 중지됩니다(샘플 데이터가 있거나 없음). 화면에 오류가 표시되지 않습니다.

## 원인

이 문제의 일반적인 원인은 다음과 같습니다.

* [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)에 대한 PHP 설정
* nginx 및 Varnish에 대한 시간 제한 값

## 해결 방법:

다음 사항을 모두 적절히 설정하십시오.

### 모든 웹 서버 및 Vannish {#all-web-servers-and-varnish}

1. [`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software) 파일을 사용하여 `php.ini`을(를) 찾습니다.
1. `root` 권한이 있는 사용자는 텍스트 편집기에서 `php.ini`을(를) 엽니다.
1. `max_execution_time` 설정을 찾습니다.
1. 값을 `18000`(으)로 변경합니다.
1. 변경 내용을 `php.ini`에 저장하고 텍스트 편집기를 종료합니다.
1. Apache 다시 시작:

   * CentOS: `service httpd restart`
   * 우분투: `service apache2 restart`

   nginx 또는 Vannish를 사용하는 경우 다음 섹션을 계속합니다.

### nginx만 {#nginx-only}

nginx를 사용하는 경우 다음과 같이 포함된 `nginx.conf.sample`을(를) 사용하거나 nginx 호스트 구성 파일의 시간 제한 설정을 `location ~ ^/setup/index.php` 섹션에 추가하십시오.

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

nginx 다시 시작: `service nginx restart`

### 니스만 {#varnish-only}

Vannish를 사용하는 경우 `default.vcl`을(를) 편집하고 다음과 같이 `backend` 스타자에 시간 제한 값을 추가하십시오.

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

바니쉬를 다시 시작합니다.

```php
service varnish restart
```
