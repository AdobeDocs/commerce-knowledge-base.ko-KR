---
title: 클라우드 인스턴스에 타사 애플리케이션을 설치할 수 있습니까?
description: '아니. 클라우드 인프라 서버에서 Adobe Commerce에 타사 앱(예: WordPress 또는 Drupal)을 설치하는 것은 허용되지 않습니다. 외부 서버에서 이러한 응용 프로그램을 호스팅해야 합니다.'
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---
# 클라우드 인스턴스에 타사 애플리케이션을 설치할 수 있습니까?

아니. 클라우드 인프라 서버에서 Adobe Commerce에 타사 앱(예: WordPress 또는 Drupal)을 설치하는 것은 허용되지 않습니다. 외부 서버에서 이러한 응용 프로그램을 호스팅해야 합니다.

## 이유

### 서비스 약관

Adobe Commerce on cloud infrastructure Edition [서비스 약관](https://magento.com/legal/terms/cloud-terms)은(는) 문서 18에 다음과 같이 명시되어 있습니다.

> 고객은 Adobe Commerce 및 서비스가 소프트웨어에 직접 의존하지 않는 다른 타사 소프트웨어 애플리케이션을 호스팅하는 데 사용되지 않는다는 데 동의합니다.

클라우드 솔루션인 Adobe은 서버 보안에 대한 모든 책임을 집니다. 높은 보안을 보장하기 위해 전용 클라우드 서버에서만 Adobe Commerce 애플리케이션 호스팅을 허용합니다.

### PCI 준수

PCI 인증 레벨 1 솔루션 공급자인 클라우드 인프라의 Adobe Commerce은 PCI 데이터 보안 표준을 준수하고 다음을 확인해야 합니다.

>... 안전한 시스템 및 애플리케이션 개발 및 유지 관리
> ([PCI 준수에 대한 Adobe 접근 방식](https://magento.com/pci-compliance) 요구 사항 6, 취약성 관리 프로그램 유지 관리)

Adobe은 타사 애플리케이션의 PCI 규정 준수를 보장할 수 없으므로 이러한 앱을 클라우드 서버에 설치하는 것은 허용되지 않습니다.

## 힌트: 더 나은 통합을 위해 Commerce Marketplace 확장 사용

클라우드 인프라 응용 프로그램의 Adobe Commerce과 외부 서버에 호스팅된 타사 솔루션의 통합을 향상하기 위해 사용자의 목적에 맞는 [Commerce Marketplace](https://marketplace.magento.com) 확장을 사용하는 것이 좋습니다.
