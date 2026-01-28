---
title: Adobe AI에 대한 API 키를 구성했지만 하나의 SaaS 데이터 공간만 표시됨
description: 이 문서에서는 Adobe AI에 대한 API 키를 구성한 후 하나의 SaaS 데이터 공간만 표시되는 문제에 대한 해결 방법을 제공합니다.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 27b0836380c3040b26076b9cb81b9328cb2c9ff2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Adobe AI에 대한 API 키를 구성했지만 하나의 SaaS 데이터 공간만 표시됨

이 문서에서는 Adobe AI에 대한 API 키를 구성한 후 하나의 SaaS 데이터 공간만 표시되는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드): 모든 버전
* Magento Open Source: 모든 버전
* 확장 또는 기술(Fastly, New Relic 등), Adobe AI(제품 추천/라이브 검색)

## 문제

Adobe AI에 대한 API 키를 구성했지만 SaaS 데이터 공간은 하나만 표시됩니다.

## 원인

표시되는 SaaS 데이터 공간 수는 Commerce 라이선스에 따라 다릅니다.

* Adobe Commerce - 프로덕션 데이터 공간 1개, 테스트 데이터 공간 2개
* Magento Open Source - 프로덕션 데이터 공간 1개, 테스트 데이터 공간 없음

## 솔루션

* API 키가 계정 소유자의 계정에 생성되었는지 확인합니다. 해당 계정에 대한 공유 액세스 권한이 부여되고 자신의 계정에 키를 만들었더라도 두 개 이상의 데이터 공간을 부여하지는 않습니다.
* 계정 소유자의 계정에 키가 생성된 경우 라이센스가 활성 상태인지, 즉, 보류 중인 송장이 없는지 확인합니다.
