---
title: PHP mcrypt 확장이 제대로 설치되지 않았습니다.
description: PHP mcrypt 확장이 제대로 설치되지 않았습니다.
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP mcrypt 확장이 제대로 설치되지 않았습니다.

>[!WARNING]
>
>참고: mcrypt 라이브러리 기능은 PHP 7.1에서 [사용되지 않으며 PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php)에서 제거되었습니다.

## 세부 사항

오류에는 다음이 포함될 수 있습니다.

```php
exception 'Exception' with message 'PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] exception 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://experienceleague.adobe.com/ko/docs/commerce-operations/operational-playbook/glossary#extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## 설명

특히 운영 체제와 별개인 Linux/Apache/MySQL/PHP(LAMP) &quot;stack&quot;이 포함된 개발자 시스템에서는 mcrypt가 전혀 설치되지 않았거나 LAMP 스택의 경로에 설치되었지만 운영 체제의 경로는 설치되지 않았을 수 있습니다.

따라서 Adobe Commerce 설치 관리자에서 확장을 찾을 수 없고 설치에 실패합니다.

## 제안

다음 방법 중 하나로 mcrypt 확장이 로드되는지 확인합니다.

* 웹 서버의 루트 디렉터리에 [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) 파일을 설정하고 웹 브라우저에서 출력을 검사합니다.
* 다음 명령을 실행합니다.    `$ php -r "phpinfo();" | grep mcrypt`

mcrypt가 *설치되지 않은*&#x200B;경우 다음과 유사한 메시지가 표시됩니다.

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

경우에 따라 [명령줄](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/advanced)에서 Adobe Commerce 소프트웨어를 설치하고 mcrypt가 설치된 LAMP 스택에 대한 전체 경로를 지정해야 할 수 있습니다.
