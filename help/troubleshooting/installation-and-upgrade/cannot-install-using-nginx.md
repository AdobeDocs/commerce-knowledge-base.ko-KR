---
title: nginx를 사용하여 설치할 수 없음
description: 이 문서에서는 nginx 웹 서버를 사용할 때 실패한 Adobe Commerce 설치에 대한 수정 사항을 제공합니다.
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
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
source-wordcount: '95'
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

[명령줄](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/advanced)을 사용하여 Adobe Commerce 소프트웨어를 설치합니다.
