---
title: 초기 알파 발러 모듈 사용으로 인한 배포 오류
description: 기능이 현재 초기 알파 개발 단계에 있으므로 판매자는 프로덕션 환경에서 Baler 모듈을 사용할 때 배포 오류를 경험합니다.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# 초기 알파 발러 모듈 사용으로 인한 배포 오류

기능이 현재 초기 알파 개발 단계에 있으므로 판매자는 프로덕션 환경에서 Baler 모듈을 사용할 때 배포 오류를 경험합니다.

>[!WARNING]
>
>초기 알파 Baler Javascript 번들링은 프로덕션에서 사용할 준비가 되지 않았으며 사용자 자신의 위험으로 사용됩니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라 2.3.x 및 2.4.x의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.3.x 및 2.4.x.

## 문제

현재 초기 알파 개발 단계이므로 판매자가 프로덕션 환경에서 Baler 모듈을 사용하는 것은 권장되지 않습니다. 이를 사용하면 배포 오류가 발생할 수 있습니다.

<u>재현 단계</u>:

1. 판매자는 `.magento.env.yaml` 파일의 빌드 단계에 **SCD\_USE\_BALER** 변수를 삽입하려고 하므로 Baler Javascript 번들 패키지를 사용할 수 있습니다.
1. 판매자는 `composer.json`의 `require` 섹션에도 Baler 작성기 종속성 `"magento/module-baler": "1.0.0-alpha"`을(를) 추가합니다.

<u>예상 결과</u>:

배포에 성공했습니다.

<u>실제 결과</u>:

판매자는 클라우드의 배포 로그(`<project home>/var/log/cloud.log`)에 정적 콘텐츠 배포 단계에서 다음 오류 메시지를 표시합니다.

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## 원인

Baler 모듈은 현재 초기 알파 개발 단계이며, Baler 확장 설치 프로세스는 복잡하다.

## 솔루션

[Github/Baler/Baler/Getting with the alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md)에서 기존 Baler Alpha Magento 설명서를 검토할 수 있습니다. 그러나 이는 생산 용도로 사용할 준비가 되지 않았으며, 자신의 책임하에 사용됩니다. 대신 파일 최적화를 위해 Adobe Commerce의 기본 제공 번들(기본 번들)을 사용하여 Javascript(JS) 파일을 병합하거나 번들로 묶는 것이 좋습니다.

* 관리에서 병합 또는 번들링을 켤 수 있습니다(병합 및 번들링은 동시에 활성화할 수 없음). **스토어** > **설정** > **구성** > **고급** > **개발자** > **JavaScript 설정**.
* 명령줄 `php -f bin/magento config:set dev/js/enable_js_bundling 1`에서 Adobe Commerce 기본 제공 번들(기본 번들)을 사용하도록 설정할 수도 있습니다.

자세한 내용은 [클라우드 인프라 및 Adobe Commerce 온-프레미스의 Adobe Commerce에서 CSS 및 Javascript 파일 최적화](https://support.magento.com/hc/en-us/articles/360044482152)를 참조하세요.
