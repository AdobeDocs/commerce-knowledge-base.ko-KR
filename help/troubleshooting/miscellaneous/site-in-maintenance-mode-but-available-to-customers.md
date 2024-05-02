---
title: 사이트가 유지 관리 모드이지만 고객이 사용 가능
description: 이 문서에서는 유지 관리 모드가 활성화된 경우(클라우드 인프라의 Adobe Commerce 문제)에 대한 수정 사항을 제공하지만 고객은 상점 전면을 계속 사용할 수 있습니다.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# 사이트가 유지 관리 모드이지만 고객이 사용 가능

이 문서에서는 유지 관리 모드가 활성화된 경우(클라우드 인프라의 Adobe Commerce 문제)에 대한 수정 사항을 제공하지만 고객은 상점 전면을 계속 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

<u>재현 단계:</u>

1. 사이트에 대한 유지 관리 모드를 활성화합니다.
1. 상점 앞으로 이동합니다.

<u>예상 결과:</u>

유지 관리 페이지가 표시됩니다.

<u>실제 결과:</u>

상점 첫 페이지는 평소와 같이 표시됩니다.

## 원인

페이지가 여전히 캐시되므로 유지 관리 페이지가 표시되지 않습니다.

## 유지 관리 모드에 있음에도 불구하고 사이트에 대한 솔루션이 표시됨

1. SSH를 환경에 추가합니다.
1. 실행 `php bin/magento cache:clean` 명령입니다.

## 관련 읽기

[유지 관리 모드 활성화 또는 비활성화](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) 개발자 설명서에서 확인할 수 있습니다.
