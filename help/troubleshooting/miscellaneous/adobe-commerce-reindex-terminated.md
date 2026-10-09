---
title: 'Adobe Commerce cloud: 리색인이 ''중단됨'' 메시지로 종료됨'
description: '* 클라우드 인프라의 Adobe Commerce(모든 버전)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '235'
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
1. 이전에 수행한 적이 없는 경우 향상된 통합 환경으로 업그레이드를 요청하십시오. 업그레이드가 수행되면 제한되는 환경 수에 대한 제한 사항을 숙지하십시오. 자세한 내용은 지원 기술 자료에서 [통합 환경 개선 요청 - Pro 및 Starter](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-27242) 문서를 참조하십시오.

## 관련 읽기:

개발자 설명서에서:

* [Pro 아키텍처 > 통합 환경](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [스타터 아키텍처 > 스테이징 환경](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
