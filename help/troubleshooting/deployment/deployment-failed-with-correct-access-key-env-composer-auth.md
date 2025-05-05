---
title: env:COMPOSER_AUTH 또는 auth.json에 올바른 액세스 키가 있어 배포가 실패합니다.
description: 이 문서에서는 "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip 파일을 다운로드할 수 없음(HTTP/1.1 404 찾을 수 없음)" 오류와 함께 배포가 실패하는 경우 발생하는 문제에 대한 해결 방법을 제공합니다.
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 2a1c97c65282d03010bffabbcd2d1be7fb9ff9a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# env:COMPOSER_AUTH 또는 auth.json에 올바른 액세스 키가 있어 배포가 실패합니다.

이 문서에서는 [배포 로그](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log)에서 아래와 같은 오류와 함께 배포가 실패하는 경우 발생하는 문제에 대한 해결 방법을 제공합니다.

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce 2.4.x

## 문제

<u>재현 단계</u>:

배포를 시도합니다.

<u>예상 결과</u>:

을(를) 배포했습니다.

<u>실제 결과</u>:

>[!NOTE]
>
>예제 오류입니다. 배포하는 Adobe Commerce 버전에 따라 다른 파일을 나타내는 오류가 발생할 수 있습니다.

을 배포하지 못했습니다. [배포 로그](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log)에 *https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip 파일을 다운로드할 수 없습니다(HTTP/1.1 404 찾을 수 없음)*.

### 원인

다음 위치 중 하나에 있는 지정된 작성기 액세스 키에 코드에 대한 액세스 권한이 없을 수 있습니다.

* 프로젝트 수준의 `env:COMPOSER_AUTH` 변수
* `auth.json file`에서 `env:COMPOSER_AUTH` 변수보다 우선합니다.

### 솔루션

프로젝트 수준에서 `env:COMPOSER_AUTH` 변수를 업데이트하고 코드에 액세스할 수 있는 키로 구성되었는지 확인하십시오.

단계는 Commerce on Cloud Infrastructure Guide의 [변수 수준](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/env/variable-levels)을 참조하세요.

## 관련 읽기

* [클라우드 저장소의 Adobe Commerce에 액세스할 수 없습니다. 배포 시 403 금지됨 또는 404 찾을 수 없음 오류](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [배포 오류: 다운로드 중 오류 7.. 포트 443: 연결이 거부되었습니다.](/help/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce.md)
