---
title: 사이트가 유지 관리 모드이지만 고객이 사용 가능
description: 이 문서에서는 유지 관리 모드가 활성화된 경우(클라우드 인프라의 Adobe Commerce 문제)에 대한 수정 사항을 제공하지만 고객은 상점 전면을 계속 사용할 수 있습니다.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
1. `php bin/magento cache:clean` 명령을 실행합니다.

## 관련 읽기

개발자 설명서에서 [유지 관리 모드를 사용하거나 사용하지 않도록 설정](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/maintenance-mode).
