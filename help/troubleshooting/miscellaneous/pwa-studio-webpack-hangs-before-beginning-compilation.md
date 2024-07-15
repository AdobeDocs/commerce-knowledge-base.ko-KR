---
title: 'PWA Studio: 컴파일을 시작하기 전에 Webpack 중단'
description: 이 문서에서는 Progressive Web App Studio(PWA Studio)에서 컴파일을 시작하기 전에 Javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)이 오랫동안 중단되는 경우에 대한 제안 해결 방법에 대해 설명합니다.
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: 컴파일을 시작하기 전에 Webpack이 중단됨

이 문서에서는 Progressive Web App Studio(PWA Studio)에서 컴파일을 시작하기 전에 Javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)이 오랫동안 중단되는 경우에 대한 제안 해결 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* PWA Studio

## 문제

[pwa-buildpack의 최신 릴리스 확인](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack) 및

```yaml
pwa-buildpack
```

버전 번호는 `package.json` 파일 이름 목록 옆에 있습니다. 이전 버전의 가 있는 경우

```yaml
pwa-buildpack
```

프로젝트에서 컴파일을 시작하기 전에 웹 팩이 오래 걸릴 수 있습니다.

<u>재현 단계</u>:

<u>필수 구성 요소</u>: 로컬 Adobe Commerce 인스턴스로 Venia와 같은 PWA Studio 상점(storefront)을 설정하고

```yaml
build
```

또는

```yaml
watch
```

명령입니다.

<u>예상 결과</u>:

* 을 사용하는 경우    ```yaml    build    ```    명령을 실행하면 일반적으로 Venia에 대한 빌드 아티팩트가 생성됩니다.
* 을 사용하는 경우    ```yaml    watch    ```    여긴 베니아 점포가 정상적으로 시작됩니다

<u>실제 결과</u>:

사용자

```yaml
build
```

또는

```yaml
watch
```

명령이 정지된 것처럼 보이고 완료되지 않으며 오류가 표시되지 않습니다.

## 솔루션

다음 명령을 사용하여 프로젝트를 업데이트합니다.

```yaml
yarn upgrade
```

다음 명령을 사용하여 시스템에 현재 버전의 openssl이 있는지 확인합니다.

```yaml
openssl version
```

버전은 1.0 이상이어야 합니다(OSX High Sierra의 경우 LibreSSL 2).

OSX의 경우 [Homebrew](https://brew.sh/), Windows의 경우 [Chocolatey](https://chocolatey.org/) 또는 Linux 배포판의 패키지 관리자로 더 높은 버전의 OpenSSL을 설치할 수 있습니다.

## 관련 읽기

* [Javascript Webpack: 개념](https://webpack.js.org/concepts/)
* [Venia storefront 설정](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA Buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [buildpack 명령줄 인터페이스](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [도구 및 라이브러리: buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
