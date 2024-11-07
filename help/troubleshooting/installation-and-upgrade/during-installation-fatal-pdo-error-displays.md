---
title: 설치하는 동안 치명적인 PDO 오류가 표시됩니다.
description: 이 문서에서는 설치하는 동안 치명적인 PDO 오류에 대한 예외 사항을 해결합니다.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# 설치하는 동안 치명적인 PDO 오류가 표시됩니다.

이 문서에서는 설치하는 동안 치명적인 PDO 오류에 대한 예외 사항을 해결합니다.

## 문제

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## 솔루션

[필요한 PHP 확장 기능](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)을 모두 설치하십시오.
