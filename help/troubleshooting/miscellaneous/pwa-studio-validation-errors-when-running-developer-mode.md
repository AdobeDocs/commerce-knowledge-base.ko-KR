---
title: 'PWA Studio: 개발자 모드 실행 시 유효성 검사 오류 발생'
description: 이 항목에서는 이전에 venia-concept(Venia는 PWA 상점)를 만들지 않았기 때문에 Adobe Commerce용 Progressive Web App(PWA) Studio에서 개발자 모드를 실행할 때 유효성 검사 오류가 발생하는 경우의 솔루션에 대해 설명합니다. 환경 파일입니다. 이 파일에는 로컬 개발 환경에 대한 변수가 있습니다.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: 개발자 모드를 실행할 때 유효성 검사 오류 발생

이 항목에서는 이전에 venia-concept(Venia는 PWA 상점)를 만들지 않았기 때문에 Adobe Commerce용 Progressive Web App(PWA) Studio에서 개발자 모드를 실행할 때 유효성 검사 오류가 발생하는 경우의 솔루션에 대해 설명합니다. 환경 파일입니다. 이 파일에는 로컬 개발 환경에 대한 변수가 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce PWA Studio

## 문제

<u>재현할 단계</u>:

* Adobe Commerce용 PWA Studio에서 개발자 모드를 실행합니다.

<u>예상 결과</u>:

* PWA Studio 서버가 정상적으로 시작됩니다.

<u>실제 결과</u>:

* 다음과 유사할 수 있는 유효성 검사 오류가 표시됩니다.

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## 원인

로컬 개발 환경에 대한 환경 변수 파일이 없습니다. 아래 명령이 생성하는 파일에는 로컬 개발 환경에 대한 변수가 저장됩니다.

## 솔루션

명령을 실행해야 합니다

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

로컬 개발 환경에 대한 변수를 저장할 파일을 생성하기 위해 루트 디렉토리에서 를 선택합니다.

## 관련 읽기

* [Adobe Commerce 설명서 PWA Studio](https://magento.github.io/pwa-studio/)
* [Venia Storefront(개념)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
