---
title: nginx를 사용하여 설치할 수 없음
description: 이 문서에서는 nginx 웹 서버를 사용할 때 실패한 Adobe Commerce 설치에 대한 수정 사항을 제공합니다.
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# nginx를 사용하여 설치할 수 없음

이 문서에서는 nginx 웹 서버를 사용할 때 실패한 Adobe Commerce 설치에 대한 수정 사항을 제공합니다.

## 문제

Nginx 웹 서버를 사용하고 Adobe Commerce 소프트웨어를 설치하려고 하면 설치에 실패하는 경우가 있습니다.

## 솔루션

`var/report` 디렉터리에서 다음 오류가 발생하여 문제를 확인할 수 있습니다.

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### 해결 방법

[명령줄](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced)을 사용하여 Adobe Commerce 소프트웨어를 설치합니다.
