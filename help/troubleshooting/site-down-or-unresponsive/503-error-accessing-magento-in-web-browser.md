---
title: 웹 브라우저에서 Adobe Commerce에 액세스하는 동안 503 오류 발생
description: 이 문서에서는 Adobe Commerce 상점 및/또는 관리자에 액세스하려고 할 때 503 오류가 발생하는 문제에 대해 가능한 해결 방법을 제공합니다.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 웹 브라우저에서 Adobe Commerce에 액세스하는 동안 503 오류 발생

이 문서에서는 Adobe Commerce 상점 및/또는 관리자에 액세스하려고 할 때 503 오류가 발생하는 문제에 대해 가능한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce 2.3.x

## 문제 {#symptoms}

<u>재현 단계</u>

(필수 구성 요소: 저장소가 [유지 관리 모드](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show)에 있지 않은지 확인하십시오.)

웹 브라우저에서 Commerce 관리자 또는 상점 페이지로 이동합니다.

<u>예상 결과</u>

페이지가 로드됩니다.

<u>실제 결과</u>

HTTP 503(서비스를 사용할 수 없음) 오류가 발생합니다. Apache `error.log`에 다음 메시지가 포함되어 있습니다.

*잘못된 명령 &#39;Order&#39;가 서버 구성에 포함되지 않은 모듈에 의해 정의되었거나 철자가 잘못되었을 수 있습니다.*

## 원인 {#details}

Apache 2.4 호환성 모듈 `mod_access_compat`이(가) 비활성화되어 Adobe Commerce URL 다시 쓰기가 제대로 작동하지 않습니다.

## 솔루션 {#suggested-solution}

&#39;루트&#39; 권한을 가진 사용자로 다음을 실행하여 `mod_access_compat` Apache 모듈을 사용하도록 설정하고 Apache를 다시 시작하십시오.

```bash
a2enmod access_compat
service <name> restart
```

CentOS에서,

```bash
<name>
```

은(는)

```bash
httpd
```

. 우분투에서,

```bash
<name>
```

은(는)

```bash
apache2
```

.

## 관련 읽기 {#additional-resources}

* [mod\_access\_compat에 대한 Apache 설명서](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [mod\_authz\_host에 대한 Apache 설명서](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Apache 정의 안내서에서 주문, 허용, 거부](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
