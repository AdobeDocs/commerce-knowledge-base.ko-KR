---
title: 선택적 샘플 데이터를 설치하는 중 오류 발생
description: 이 항목에서는 선택적 샘플 데이터 설치를 통해 발생할 수 있는 오류 해결 방법에 대해 설명합니다.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# 선택적 샘플 데이터를 설치하는 중 오류 발생

이 항목에서는 선택적 샘플 데이터 설치를 통해 발생할 수 있는 오류 해결 방법에 대해 설명합니다.

## 증상(파일 시스템 권한)

설치 마법사를 사용하여 샘플 데이터를 설치하는 동안 콘솔 로그에 오류가 발생했습니다.

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

이러한 예외는 파일 시스템 권한 설정에서 발생합니다.

### 솔루션

`root` 권한이 있는 사용자로 [파일 시스템 소유권 및 권한을 다시 설정](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html)합니다.

## 증상(프로덕션 모드)

현재 [프로덕션 모드](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html)로 설정된 경우 [magento sampledata:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html) 명령을 사용하면 샘플 데이터 설치가 실패합니다.

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### 솔루션

프로덕션 모드에서 샘플 데이터를 설치하지 마십시오. 개발자 모드로 전환하고 일부 `var` 디렉터리를 지운 후 다시 시도하십시오.

[Adobe Commerce 파일 시스템 소유자](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html)(으)로 표시된 순서대로 다음 명령을 입력하십시오.

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## 증상(보안)

선택적 샘플 데이터를 설치하는 동안 다음과 유사한 메시지가 표시됩니다.

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### 솔루션

샘플 데이터 설치 중에 다음과 같은 리소스를 사용하여 SELinux를 비활성화합니다.

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [CentOS 설명서](https://docs.centos.org/en-US/docs/)

## 증상(분지 발생)

다음과 같은 기타 오류가 표시됩니다.

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### 솔루션

Adobe Commerce 개발 분기에 샘플 데이터를 사용하는 것과 관련하여 알려진 문제가 있습니다. 대신 마스터 분기를 사용합니다. 다음과 같이 마스터 분기로 전환할 수 있습니다.

```php
cd <magento_root>
git checkout master
git pull origin master
```

## 증상(max_execution_time)

샘플 데이터 설치가 완료되기 전에 설치가 중지됩니다. 예제는 다음과 같습니다.

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

샘플 데이터 설치가 완료되지 않았습니다.

이 오류는 PHP 스크립트의 최대 구성 실행 시간을 초과할 때 발생합니다. 샘플 데이터를 로드하는 데 시간이 오래 걸릴 수 있으므로 설치하는 동안 값을 늘릴 수 있습니다.

### 솔루션

`root` 권한이 있는 사용자는 `php.ini`을(를) 수정하여 `max_execution_time`의 값을 600 이상으로 늘리십시오. (600초는 10분입니다. 원하는 대로 값을 늘릴 수 있습니다.) 설치가 완료된 후 `max_execution_time`을(를) 이전 값으로 다시 변경해야 합니다.

`php.ini`의 위치를 모를 경우 다음 명령을 입력하십시오.

```php
php --ini
```

`Loaded Configuration File`의 값은 수정해야 하는 `php.ini`입니다.

>[!NOTE]
>
>이 문서에는 일부 사람들이 인종차별주의자, 성차별주의자 또는 억압적이라고 생각할 수 있고 독자로 하여금 상처받거나, 트라우마를 받거나, 환영받지 못하게 만들 수 있는 업계 표준 소프트웨어 용어가 여전히 포함되어 있을 수 있다는 것을 알고 있습니다. Adobe이 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하고 있습니다.
