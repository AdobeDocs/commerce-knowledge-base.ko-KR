---
title: 'PWA Studio: 브라우저가 생성된 SSL 인증서를 신뢰하지 않음'
description: 이 문서에서는 개발 중에 PWA Studio 저장소의 로컬 인스턴스로 이동할 때 브라우저에서 신뢰할 수 없고 생성된 SSL 인증서 경고에 대한 솔루션을 제공합니다.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio: 브라우저가 생성된 SSL 인증서를 신뢰하지 않음

이 문서에서는 개발 중에 PWA Studio 저장소의 로컬 인스턴스로 이동할 때 브라우저에서 신뢰할 수 없고 생성된 SSL 인증서 경고에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce PWA Studio

## 문제

브라우저가 로컬 PWA Studio 상점 첫 화면의 생성된 SSL 인증서를 신뢰하지 않습니다.

## 원인

개발/스테이징 사이트로 이동 중.

## 솔루션

storefront 프로젝트에서 로컬 개발 인스턴스에 사용자 지정 호스트 이름 및 SSL 인증서를 추가하는 명령을 실행합니다.

```sh
yarn buildpack create-custom-origin ./
```

인증서 생성은 [devcert](https://github.com/davewasmer/devcert)에서 처리됩니다. OpenSSL에 따라 다르므로 다음 명령을 사용하여 시스템에 현재 버전의 openssl이 있는지 확인합니다.

`openssl version`

버전은 1.0 이상이어야 합니다(또는 OSX High Sierra의 경우 LibreSSL 2).

OSX의 경우 [Homebrew](https://brew.sh/), Windows의 경우 [Chocolatey](https://chocolatey.org/) 또는 Linux 배포판의 패키지 관리자로 더 높은 버전의 OpenSSL을 설치할 수 있습니다.

Linux를 실행 중인 경우 `libnss3-tools`(또는 이에 상응하는)이(가) 시스템에 설치되어 있는지 확인하십시오. [devcert](https://github.com/davewasmer/devcert#skipcertutil) readme의 이 섹션에 추가 정보가 제공됩니다.

일부 사용자가 인증서 재생성을 트리거하기 위해 devcert 폴더를 삭제하는 것을 제안했습니다.

* macOS 사용자의 경우 이 폴더는 일반적으로 `{{~/Library/Application Support/devcert }}`에 있습니다.
* Windows 사용자의 경우 이 폴더는 일반적으로 `${User}\AppData\Local\devcert`에 있습니다.

## 지원 기술 자료의 관련 읽기

* [PWA Studio: 자체 서명된 인증서 신뢰 오류](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: 컴파일을 시작하기 전에 Webpack이 중단됨](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: 브라우저에 &quot;프록시 대상 불가&quot; 오류 표시](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: 개발자 모드를 실행할 때 유효성 검사 오류 발생](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
