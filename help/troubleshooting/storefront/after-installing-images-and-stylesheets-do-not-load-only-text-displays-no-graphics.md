---
title: 설치 후 이미지와 스타일시트는 로드되지 않고 텍스트만 표시되고 그래픽은 표시되지 않습니다
description: 이 문서에서는 Adobe Commerce 설치 후 스타일시트 및 이미지가 로드되지 않는 문제에 대한 가능한 원인 및 해결 방법에 대해 설명합니다.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# 설치 후 이미지와 스타일시트는 로드되지 않고 텍스트만 표시되고 그래픽은 표시되지 않습니다

이 문서에서는 Adobe Commerce 설치 후 스타일시트 및 이미지가 로드되지 않는 문제에 대한 가능한 원인 및 해결 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## 문제

<u>재현 단계</u>

1. Adobe Commerce을 설치합니다.
1. 상점 또는 관리자로 이동합니다.

<u>예상 결과</u>

스타일이 적용되어 UI 요소가 누락된 스타일처럼 보이지 않습니다.

<u>실제 결과</u>

스타일이 올바르게 적용되지 않고 그래픽이 누락되었습니다.

## 원인

잘못된 기본 URL 또는 서버 재작성(CentOS, Ubuntu)이 제대로 설정되지 않았으므로 이미지 및 스타일시트에 대한 경로가 올바르지 않습니다.

이 경우 확인하려면 웹 브라우저 검사기를 사용하여 정적 에셋에 대한 경로를 확인하고 해당 에셋이 Adobe Commerce 또는 Magento Open Source 파일 시스템에 있는지 확인하십시오.

정적 자산은 `frontend` 및 `adminhtml` 디렉터리 내의 `<magento_root>/pub/static/` 아래에 있습니다.

## 솔루션

다음은 사용하는 소프트웨어와 문제의 원인에 따라 가능한 해결 방법입니다.

* Apache 웹 서버를 사용하는 경우 [서버 재작성](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) 설정과 Adobe Commerce/Magento Open Source 서버의 기본 URL을 확인하고 다시 시도하십시오. Apache `AllowOverride` 지시문을 잘못 설정하면 정적 파일이 올바른 위치에서 제공되지 않습니다.
* nginx 웹 서버를 사용하는 경우 [가상 호스트 파일을 구성](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu)하십시오. nginx 가상 호스트 파일은 다음 기준을 충족해야 합니다.
   * `include` 지시문은 Adobe Commerce/Magento Open Source 설치 디렉터리의 샘플 nginx 구성 파일을 가리켜야 합니다. 예:    `include /var/www/html/magento2/nginx.conf.sample;`
   * `server_name` 지시문은 Adobe Commerce/Magento Open Source 설치 시 지정한 기본 URL과 일치해야 합니다. 예: `server_name 192.186.33.10;`
* 응용 프로그램이 [프로덕션 모드](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode)에 있는 경우 `magento setup:static-content:deploy` 명령을 사용하여 정적 보기 파일을 배포해 보십시오. 정적 파일 배포에 대한 자세한 내용은 개발자 설명서에서 [정적 보기 파일 배포](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html)를 참조하십시오.
