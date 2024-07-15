---
title: 배포 후 env.php에 .magento.env.yaml 변경 사항이 표시되지 않음
description: 이 문서에서는 배포 후 .magento.env.yaml 파일의 변경 내용이 app/etc/env.php에 반영되지 않는 문제에 대한 해결 방법을 제공합니다.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 배포 후 env.php에 .magento.env.yaml 변경 사항이 표시되지 않음

>[!NOTE]
>
>이 문제가 있는 경우 ece-tools 2002.1.5로 업그레이드하여 문제를 해결하십시오. 2002.1.5에는 각 배포에서 opcache를 다시 설정하는 기능이 있으므로 `opcache.enable_cli=1` 설정을 변경할 필요가 없습니다. 업그레이드하지 않으려면 솔루션에서 아래에 설명된 대로 해결 단계를 수행해야 합니다.

이 문서에서는 배포 후 `.magento.env.yaml` 파일의 변경 내용이 `app/etc/env.php`에 반영되지 않는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce(모든 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## 문제

`.magento.env.yaml` 파일에서 변경한 내용은 생성된 `app/etc/env.php`에 영향을 주지 않습니다.

<u>재현 단계:</u>

`.magento.env.yaml`에서 값을 변경하고 서버로 푸시합니다. 여기서 현재 체크 아웃된 환경에 대한 구성(및 배포 설정)을 정의해야 합니다. 단계는 개발자 설명서에서 [환경 변수 > 변수 배포](https://devdocs.magento.com/cloud/env/variables-deploy.html)를 참조하십시오.

<u>예상 결과:</u>

`.magento.env.yaml` 파일에서 변경한 내용은 생성된 `app/etc/env.php`에 영향을 줍니다.

<u>실제 결과:</u>

배포 후 변경 내용은 `app/etc/env.php` 변수에 영향을 주지 않습니다.

## 원인

`php.ini` 파일에 있는 `opcache.enable_cli` 매개 변수의 값이 잘못되었기 때문일 수 있습니다.

## 솔루션

1. 시스템이 [Adobe Commerce 성능 모범 사례 > 소프트웨어 권장 사항](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html)에 따라 구성되어 있는지 확인하십시오.
1. 다음을 실행하여 `php.ini`의 `opcache.enable_cli` 지시문이 `0`(으)로 설정되어 있는지 확인: `php -i | grep opcache.enable_cli`
1. 출력이 `opcache.enable_cli=1`(으)로 표시되는 경우 프로젝트 루트 디렉터리에서 `php.ini` 파일을 편집하고 `opcache.enable_cli=1`을(를) `opcache.enable_cli=0`(으)로 변경합니다.
1. 프로젝트를 다시 배포합니다.

## 관련 읽기

* [Adobe Commerce용 클라우드 > 빌드 및 배포](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
