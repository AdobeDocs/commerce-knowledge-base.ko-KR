---
title: xdebug 설치에 영향을 주는 알려진 문제
description: 이 문서에서는 선택적 PHP 확장 'xdebug'를 사용할 때 예외 오류가 발생하는 경우를 위한 해결 방법을 제공합니다.
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# xdebug 설치에 영향을 주는 알려진 문제

이 문서에서는 선택적 PHP 확장 `xdebug`을(를) 사용할 때 예외 오류가 발생하는 경우에 대한 해결 방법을 제공합니다.

* 설치 중
* 성공적인 설치 후 Commerce 관리자 또는 상점 첫 화면에 액세스

샘플 예외:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

이 문제를 해결하려면 다음을 수행할 수 있습니다.

* `xdebug` 확장을 사용하지 않도록 설정합니다.
* `xdebug.max_nesting_level`의 값을 200 이상의 값으로 설정하십시오. 자세한 내용은 [xdebug 설명서](http://xdebug.org/docs/basic#max_nesting_level)를 참조하십시오.

`xdebug`의 구성을 변경하거나 사용하지 않도록 설정한 후 Apache를 다시 시작하십시오.

* CentOS: `sudo service httpd restart`
* 우분투: `sudo service apache2 restart`
