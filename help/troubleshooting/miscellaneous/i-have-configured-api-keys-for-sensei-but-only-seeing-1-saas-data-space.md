---
title: Adobe AI API 키를 구성한 후 여러 SaaS 데이터 공간을 볼 수 없음
description: 이 문서에서는 Adobe AI에 대한 API 키를 구성한 후 하나의 SaaS 데이터 공간만 표시되는 문제에 대한 솔루션을 제공합니다.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 61f5a526a0c36c91739103c0802bc9794a425f38
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Adobe AI API 키를 구성한 후 여러 SaaS 데이터 공간을 볼 수 없음

Adobe AI 서비스(제품 추천 또는 라이브 검색) 또는 Adobe Commerce용 결제 서비스 와 같은 Commerce 서비스에 대한 API 키를 구성하면 Commerce 서비스 커넥터에 여러 SaaS 데이터 공간이 표시됩니다. 제품 권한 및 배포 유형에 따라 커넥터는 하나의 SaaS 데이터 공간만 표시하므로 예상되는 동작입니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드): 모든 버전
* Magento Open Source: 모든 버전
* 확장 또는 기술(Fastly, New Relic 등), Adobe AI(제품 추천/라이브 검색)

## 문제

Adobe AI API 키를 구성하면 시스템에 하나의 SaaS 데이터 공간만 표시됩니다.

## 원인

사용 가능한 SaaS 데이터 공간 수는 Commerce 계정에 연결된 제품 권한 및 사용 중인 서비스 유형에 따라 다릅니다.

## 솔루션

일반적으로 사용 가능한 SaaS 데이터 공간 수는 Commerce 라이선스에 따라 다릅니다.

* Adobe Commerce: 프로덕션 데이터 공간 1개와 테스트 데이터 공간 2개
* Magento Open Source: 프로덕션 데이터 공간 1개(테스트 데이터 공간 없음)

결제 서비스의 기본 동작은 다음과 같습니다.

* Adobe Commerce(*Cloud 또는 온-프레미스*)의 결제 서비스에는 기본적으로 3개의 데이터 공간이 있습니다.
* 프로덕션 데이터 공간 1개
* 두 개의 테스트 데이터 공간
* Magento Open Source의 결제 서비스에는 기본적으로 하나의 데이터 공간이 있습니다

여러 클라우드 프로젝트 또는 온프레미스(*라이브/프로덕션*) 설치를 보유한 고객은 지원 요청을 제출하여 각 프로젝트 또는 인스턴스에 대한 추가 프로덕션 및 테스트 데이터 공간을 요청할 수도 있습니다.

Adobe 결제 서비스를 사용하는 Magento Open Source 고객도 추가 데이터 공간을 요청할 수 있습니다. 테스트 데이터 공간을 추가하려면 지원 요청을 제출하기 전에 결제 팀에 연락하여 사전 승인을 받으십시오.

>[!NOTE]
> * 여러 환경에서 동일한 SaaS 데이터 공간을 동시에 사용하지 마십시오. 운영 또는 테스트 데이터 공간을 여러 환경에서 재사용하는 경우 데이터가 혼합될 수 있으며 정리가 필요할 수 있습니다.
> * Adobe Commerce(*Cloud/On-Prem*)의 결제 서비스에는 기본적으로 3개의 데이터 공간이 있습니다.
> * Magento Open Source의 결제 서비스에는 기본적으로 하나의 데이터 공간이 있습니다.
> 추가 데이터 공간을 요청하려면:
> * Adobe 결제 서비스를 사용하는 Magento Open Source 고객은 추가 데이터 공간을 요청할 수 있습니다. 테스트 데이터 공간을 얻으려면 지원 요청을 제출하기 전에 결제 팀에 연락하여 사전 승인을 받으십시오.
> * 여러 클라우드 프로젝트 또는 온프레미스(*라이브/프로덕션*) 설치를 보유한 고객은 지원 요청을 제출하여 각 프로젝트 또는 인스턴스에 대한 추가 프로덕션 및 테스트 데이터 공간을 요청할 수도 있습니다.

## 관련 읽기

[SaaS 데이터 공간 프로비저닝](https://experienceleague.adobe.com/ko/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
