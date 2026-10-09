---
title: 사용자 정의 서버측 스크립트가 pub 미디어 디렉토리에서 실행되지 않음
description: '이 문서에서는 클라우드 인프라에 있는 Adobe Commerce 애플리케이션의 "./pub/media/" 디렉토리에 사용자 정의 서버측 스크립트가 실행되지 않는 경우에 대한 수정 사항을 제공합니다. `./pub/media/` 디렉토리가 쓰기 가능하므로 예상되는 보안 제한입니다. 스크립트를 실행 가능한 디렉토리로 만들려면 쓰기 불가능한 디렉토리(예: ''./app/code/'' 또는 ''./pub/'')에 스크립트를 배치합니다.'
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---
# 사용자 정의 서버측 스크립트가 pub 미디어 디렉토리에서 실행되지 않음

이 문서에서는 클라우드 인프라에 있는 Adobe Commerce 애플리케이션의 `./pub/media/` 디렉터리에 배치되었을 때 사용자 지정 서버측 스크립트가 실행되지 않는 경우에 대한 수정 사항을 제공합니다. `./pub/media/` 디렉터리는 쓰기 가능하므로 이는 예상되는 보안 제한입니다. 스크립트를 실행 가능한 디렉터리로 만들려면 `./app/code/` 또는 `./pub/`과(와) 같이 쓸 수 없는 디렉터리에 스크립트를 배치하십시오.

## 영향을 받는 버전

* 클라우드 인프라의 Adobe Commerce: 2.1.x 이상, Starter and Pro는 아키텍처, 날개 및 레거시 아키텍처를 계획합니다.

## 문제: 스크립트가 실행되지 않음

시작되면 사용자 정의 서버측 스크립트를 실행할 수 없습니다.

예를 들어 최종 사용자(Adobe Commerce 구매자)가 스크립트가 있는 `\*.php` 파일로 연결되는 링크(예: *domain.com/media/directory/script.php*)를 클릭하면 스크립트가 실행되지 않고 다운로드됩니다.

## 원인: 스크립트 파일의 위치가 잘못되었습니다.

이 문제는 스크립트 파일이 클라우드 인프라에 있는 Adobe Commerce 애플리케이션의 `./pub/media/` 디렉터리에 있을 때 발생합니다. 이는 예상되는 동작입니다. 보안 제한으로 인해 쓰기 가능한 디렉터리(`./pub/media/`)의 파일이 실행되지 않습니다.

## 해결 방법: 쓰기 불가능한 디렉토리에 스크립트 배치

`./app/code/` 또는 `./pub/`과(와) 같이 쓸 수 없는 디렉터리에 서버측 스크립트를 저장합니다.

## 관련 설명서

* 개발자 설명서에서 [Adobe Commerce용 클라우드 > 프로젝트 구조 > 쓰기 가능한 디렉터리](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories).
