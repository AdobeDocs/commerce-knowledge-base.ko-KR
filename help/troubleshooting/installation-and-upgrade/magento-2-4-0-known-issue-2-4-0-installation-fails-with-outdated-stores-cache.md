---
title: 오래된 저장소 캐시로 Adobe Commerce 2.4.0 설치에 실패함
description: 이 문서에서는 다음과 같은 오류 메시지와 함께 Adobe Commerce 2.4.0 설치에 실패하는 문제에 대한 해결 방법을 제공합니다. *기본 웹 사이트가 정의되지 않았습니다. 웹 사이트를 설정하고 다시 시도하십시오.* 콘솔에 표시됩니다.
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%
---
# 오래된 저장소 캐시로 Adobe Commerce 2.4.0 설치에 실패함

이 문서에서는 다음과 같은 오류 메시지와 함께 Adobe Commerce 2.4.0 설치에 실패하는 문제에 대한 해결 방법을 제공합니다. *기본 웹 사이트가 정의되지 않았습니다. 웹 사이트를 설정하고 다시 시도하십시오.* 콘솔에 표시됩니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0

## 문제

<u>필수 구성 요소:</u>
CLI 명령의 저장소 모듈에 대한 API에 종속성이 있는 타사 확장이 `composer.json`에서 필요에 따라 구성되어 있습니다. 이로 인해 Adobe Commerce 2.4.0을 설치하지 못하고 다음 오류 메시지가 표시됩니다. *기본 웹 사이트가 정의되지 않았습니다. 웹 사이트를 설정하고 다시 시도하십시오.* 콘솔에 표시됩니다.

## 원인

CLI 명령의 저장소에 종속된 타사 확장의 경우 문제가 나타납니다. 하나는 Amazon 판매 채널입니다.

## 솔루션

Adobe Commerce 2.4.0을 설치하기 전에 판매자는 다음을 수행해야 합니다.

1. `composer.json`에서 이러한 타사 확장을 제거합니다.
1. 확장 없이 Adobe Commerce을 설치합니다.
1. 설치 후 확장을 추가합니다.

이 문제는 2.4.1 릴리스 범위에서 수정됩니다.

## 지원 기술 자료의 관련 자료:

* [Adobe Commerce 2.4.0 알려진 문제: Klarna에 &quot;환불&quot; 레이블이 없음](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo 부분 송장 문제 활성화](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 알려진 문제: Amazon Pay 사용, 표준 체크아웃으로 돌아가기 사용 시 결제 방법 누락](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

