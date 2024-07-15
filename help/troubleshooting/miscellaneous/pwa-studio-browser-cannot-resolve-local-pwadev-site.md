---
title: 'PWA Studio: 브라우저가 .local.pwadev 사이트를 확인할 수 없음'
description: 이 문서에서는 다른 프로그램 또는 프로세스가 [host file](https://en.wikipedia.org/wiki/Hosts_(file\)을 편집하고 프로젝트 도메인의 항목을 제거한 경우에 대한 해결 방법을 제공합니다.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio: 브라우저가 .local.pwadev 사이트를 확인할 수 없습니다.

이 문서에서는 다른 프로그램 또는 프로세스가 [호스트 파일](https://en.wikipedia.org/wiki/Hosts_(file\)을 편집하고 프로젝트 도메인의 항목을 제거한 경우에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce PWA Studio

## 문제

개발/스테이징 사이트로 이동할 때 `.local.pwadev` 사이트가 표시되지 않습니다.

## 원인

PWA Studio을 사용하면 프로젝트에 대한 사용자 지정 호스트 이름과 SSL 인증서를 로컬 컴퓨터에 할당할 수 있습니다. 여기에는 컴퓨터의 호스트 파일에 `my-storefront-project-abc123.local.pwadev`과(와) 유사한 새 항목이 만들어집니다.

이 항목은 개발자의 컴퓨터에 있는 모든 브라우저에서 해당 URL에 액세스할 때 로컬 상점 프로젝트를 확인하도록 지시합니다. 다른 프로그램 또는 프로세스가 들어와서 해당 항목을 제거한 경우 브라우저가 어디로 이동할지 알 수 없으며 브라우저가 `.local.pwadev` 사이트를 확인할 수 없습니다.

## 솔루션

[호스트 파일을 수동으로 편집](https://support.rackspace.com/how-to/modify-your-hosts-file/)하여 항목을 다시 추가할 수 있지만 설치된 다른 소프트웨어를 검사하여 이전 변경 내용을 덮어쓴 내용을 확인해야 합니다.

## 지원 기술 자료의 관련 읽기

* [PWA Studio: 자체 서명된 인증서 신뢰 오류](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: 컴파일을 시작하기 전에 Webpack이 중단됨](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: 브라우저에 &quot;프록시 대상 불가&quot; 오류 표시](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: 개발자 모드를 실행할 때 유효성 검사 오류 발생](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
