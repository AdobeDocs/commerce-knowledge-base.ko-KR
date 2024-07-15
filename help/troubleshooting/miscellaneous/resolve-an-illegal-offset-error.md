---
title: 잘못된 오프셋 오류 해결
description: 이 문서에서는 Adobe Commerce 2.1 이상에서 Commerce 관리에서 새 제품을 만들 때 잘못된 오프셋 문제 해결 오류를 받는 문제를 해결할 수 있는 방법을 제공합니다.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 잘못된 오프셋 오류 해결

이 문서에서는 Adobe Commerce 2.1 이상에서 Commerce 관리에서 새 제품을 만들 때 잘못된 오프셋 문제 해결 오류를 받는 문제를 해결할 수 있는 방법을 제공합니다.

Adobe Commerce 2.1 이상에서는 Commerce 관리에서 새 제품을 만들 때 다음 오류가 표시될 수 있습니다.

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## 세부 사항

Adobe Commerce 2.1 이상 버전은 `Magento\Framework\Api\ExtensionAttributesFactory.php`의 [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) 메서드에서 `getDocComment` 유효성 검사 호출에 PHP 코드 주석을 사용합니다.

PHP OPcache를 활성화하면 기본적으로 OPcache 설정 [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments)이(가) 비활성화되어 있기 때문에 이 오류가 표시됩니다.

## 해결 방법

이 문제를 해결하려면 OPcache 구성 설정을 찾아 다음과 같이 `opcache.save_comments`을(를) 활성화합니다.

### 1단계: OPcache 구성 찾기

#### OPcache 구성 설정을 찾으려면 다음을 수행합니다.

PHP OPcache 설정은 일반적으로 `php.ini` 또는 `opcache.ini`에 있습니다. 위치는 운영 체제와 PHP 버전에 따라 달라질 수 있습니다. OPcache 구성 파일에 `[opcache]` 섹션이나 `opcache.enable` 같은 설정이 있을 수 있습니다.

다음 지침을 사용하여 찾습니다.

* Apache 웹 서버:<br>

Apache가 있는 Ubuntu의 경우 OPcache 설정은 일반적으로 `php.ini`에 있습니다.<br>
Apache 또는 nginx가 있는 CentOS의 경우 OPcache 설정은 일반적으로 `/etc/php.d/opcache.ini`에 있습니다.<br>
그렇지 않은 경우 다음 명령을 사용하여 찾습니다.

```bash
    $ sudo find / -name 'opcache.ini'
```

* nginx 웹 서버(PHP-FPM 포함): `/etc/php5/fpm/php.ini`.

`opcache.ini`이(가) 두 개 이상인 경우 모두 수정하십시오.


### 2단계: `opcache.save_comments` 사용

1. 텍스트 편집기에서 OPcache 구성 파일을 엽니다.
1. `opcache.save_comments`을(를) 찾아 필요한 경우 주석 처리를 제거합니다.
1. 해당 값이 `1`(으)로 설정되어 있는지 확인하십시오.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 웹 서버를 다시 시작합니다.

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu 및 CentOS: `service nginx restart`

1. 자동 생성할 수 있는 DI 구성 및 누락된 모든 클래스를 재생성합니다.

```bash
    $ bin/magento setup:di:compile`
```
