---
title: Redis 문제 지연 Commerce 관리자 로그인 또는 체크아웃
description: 이 문서에서는 Commerce 관리자에 로그인하거나 체크아웃 페이지를 열면 지연 또는 시간 초과(30초 이상)가 발생하는 문제를 해결하는 방법을 제공합니다. 이 문제는 Redis가 세션 저장소에 사용될 때 발생합니다.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Redis 문제 지연 Commerce 관리자 로그인 또는 체크아웃

이 문서에서는 Commerce 관리자에 로그인하거나 체크아웃 페이지를 열면 지연 또는 시간 초과(30초 이상)가 발생하는 문제를 해결하는 방법을 제공합니다. 이 문제는 Redis가 세션 저장소에 사용될 때 발생합니다.

**원인:**   [Github 문제 \#12385](https://github.com/magento/magento2/issues/12385).

**해결 방법:** 모든 버전의 Redis 및 특정 버전의 Adobe Commerce에 대한 이러한 문제를 해결하기 위해 최신 Adobe Commerce 패치로 업데이트합니다.

## 영향을 받는 버전 및 기술

* 클라우드 인프라의 Adobe Commerce 버전 2.1.11 - 2.1.13 및 2.2.1
* Adobe Commerce 온-프레미스 버전 2.1.11 - 2.1.13 및 2.2.1
* Redis, 모든 버전

클라우드 인프라 버전 [2.2.0](#h_64593789291526919876198)에서 Adobe Commerce을 사용하는 경우 해결 방법을 사용할 수 있습니다.

## 문제

Commerce 관리자에 로그인하거나 체크아웃 페이지로 진행하는 데 30초 이상 걸립니다.

이 문제는 사용자 세션이 Redis에 저장된 경우에만 발생합니다.

## 원인

Adobe Commerce은 세션 저장에 Redis를 사용할 때 일부 작업에 30초 시간 제한을 추가하는 세션 잠금 메커니즘에 문제가 있었습니다. 자세한 내용은 [Github 문제 \#12385](https://github.com/magento/magento2/issues/12385)을(를) 참조하십시오.

이 문제는 Adobe Commerce 2.1.14 및 2.2.2에서 해결되었습니다.

## 솔루션: 패치 또는 업그레이드

### 해결 방법 1: 패치 적용

패치를 받으려면 패치를 요청하는 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오. 티켓에서 Adobe Commerce 버전과 해당 패치 참조 번호를 지정합니다.

* **2.1.11 이상:** MDVA-7835
* **2.2.1:** MDVA-8128

일반(버전과 관계없음) 참조 번호는 MAGETWO-84289입니다.

### 솔루션 2: 2.1.14/2.2.2 이상으로 업그레이드

이전에 Adobe Commerce 2.2.2 이상으로 업그레이드하는 것을 고려했다면 이 업데이트 기회를 사용하여 문제를 해결할 수 있습니다.

## 해결 방법: 세션 잠금 비활성화

세션 잠금을 비활성화하려면 `env.php` 파일의 Redis 구성 섹션에서 `disable_locking`을(를) `1`(으)로 설정합니다.

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

이 솔루션은 다른 Adobe Commerce 기능에는 영향을 주지 않습니다.

### 패치를 적용한 후 해결 방법 되돌리기

수정 사항이 적용된 패치를 적용한 후에는 해결 방법이 더 이상 필요하지 않으므로 `disable_locking`을(를) `0`(으)로 되돌릴 수 있습니다.

## 클라우드 인프라 2.2.0의 Adobe Commerce: ECE-Tools v2002.0.8 이상 사용 {#h_64593789291526919876198}

버전 2002.0.3 - 2002.0.7의 [ECE-Tools](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) 배포 스크립트 패키지가 [적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=ko)되어 `disable_locking`을(를) `1`(으)로 설정하여 해결 방법이 자동으로 적용됩니다. 이렇게 하면 원래 문제가 발생하지 않는 Adobe Commerce 2.2.0에 대한 세션 잠금 메커니즘이 비활성화됩니다.

클라우드 인프라 2.2.0에서 Adobe Commerce을 실행하는 경우 ECE-Tools를 v2002.0.8 이상으로 업그레이드하십시오. 클라우드 인프라의 Adobe Commerce을 2.2.2 이상으로 업그레이드하는 것도 고려해 볼 수 있습니다.
