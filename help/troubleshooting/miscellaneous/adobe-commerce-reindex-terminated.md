---
title: '''Adobe Commerce 클라우드: 리색인이 ''중단됨'' 메시지로 종료됨'''
description: '* 클라우드 인프라의 Adobe Commerce(모든 버전)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Adobe Commerce cloud: 리인덱싱이 `Killed` 메시지로 종료됨

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

통합 분기(또는 스타터 아키텍처 프로젝트의 스테이징)에서 색인 재지정을 실행하려고 하며 프로세스가 `Killed` 메시지로 종료됩니다.

## 원인

PHP 프로세스에 메모리가 부족하기 때문에 일반적으로 발생합니다.
가장 일반적인 이유는 인스턴스에 제품, 스토어 및/또는 고객 그룹이 많이 있기 때문입니다.

## 솔루션

1. 제품 수를 줄입니다(해당되는 경우 고객 그룹 및 스토어 수 포함).
1. 동시 사용자 한 명 또는 두 명으로 사용을 제한합니다.
1. cron 작업을 비활성화하고 필요에 따라 수동으로 실행합니다.
1. 이전에 수행한 적이 없는 경우 향상된 통합 환경으로 업그레이드를 요청하십시오. 업그레이드가 수행되면 제한되는 환경 수에 대한 제한 사항을 숙지하십시오. 자세한 내용은 지원 기술 자료에서 [통합 환경 개선 요청 - Pro 및 Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 문서를 참조하십시오.

## 관련 읽기:

개발자 설명서에서:

* [Pro 아키텍처 > 통합 환경](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#cloud-arch-int)
* [시작 아키텍처 > 스테이징 환경](https://devdocs.magento.com/cloud/architecture/starter-architecture.html#cloud-arch-stage)
