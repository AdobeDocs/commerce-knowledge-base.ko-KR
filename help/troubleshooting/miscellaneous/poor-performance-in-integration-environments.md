---
title: 통합 환경의 성능 저하
description: 이 문서에서는 Pro 통합 환경 및 스타터 스테이징 환경의 성능이 저하되는 문제에 대한 해결 방법을 제공합니다.
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 통합 환경의 성능 저하

이 문서에서는 Pro 통합 환경 및 스타터 스테이징 환경의 성능이 저하되는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전:

* 클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

Pro 통합 환경 또는 스타터 스테이징 환경의 성능이 저하됩니다.

## 원인

카탈로그/데이터의 크기 또는 타사 통합/사용자 지정의 요구 사항에 따라 통합 환경에서 사용할 수 있는 리소스가 초과되었을 수 있습니다.

## 솔루션

성능 문제를 해결하려면 통합 환경에서 최상의 성능을 발휘하기 위한 모범 사례를 준수해야 합니다. 통합을 향상시키기 위해 환경 업그레이드를 요청해야 할 수도 있습니다.

먼저 환경이 [향상된 통합 구성](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-27242)에 있는지 확인합니다.

* [Pro 아키텍처](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [시작 아키텍처](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

다음 방법 중 하나를 사용하여 배포 로그를 확인합니다.

### 방법 1:

Cloud CLI를 사용하여 다음 명령을 실행합니다.

`magento-cloud activity:log -e <branch name>`

### 방법 2:

[Cloud Console](https://console.adobecommerce.com)에서 해당 환경에 대한 최신 배포 로그를 확인하십시오.

배포 로그의 끝에 이와 같은 내용이 표시되면 첫 번째 줄에는 size=XL이 표시되고 나머지 줄에는 size=L이 표시되면 고급 통합 구성에 있는 것입니다.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

고급 통합 구성에 있지 않은 경우 [개선/업그레이드를 요청](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-27242)할 수 있습니다.
이미 향상된 통합 구성을 사용하고 있거나 업그레이드 후에도 성능 문제가 발생하는 경우 통합 환경에서 최적의 성능을 위한 모범 사례를 따라야 합니다.

* [Pro 아키텍처](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [시작 아키텍처](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

위의 권장 사항을 이행한 경우 추가 지원을 받으려면 [지원 요청을 제출](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)하십시오.
