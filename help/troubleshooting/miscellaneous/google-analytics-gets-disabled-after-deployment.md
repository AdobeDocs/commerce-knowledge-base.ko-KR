---
title: 배포 후 Google Analytics이 비활성화됨
description: 이 항목에서는 배포 중에 Google Analytics에서 경험할 수 있는 일반적인 문제에 대한 해결 방법에 대해 설명합니다.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: adedf3b3-e153-47a3-ae73-b5d65067b544
    internal-label: Build system
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%
---
# 배포 후 Google Analytics이 비활성화됨

이 항목에서는 배포 중에 Google Analytics에서 경험할 수 있는 일반적인 문제에 대한 해결 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

환경 간에 코드를 배포할 때 빌드 및 배포 스크립트는 `master/production/staging` 분기가 배포되어 Google Analytics이 활성화되었는지 확인합니다. 마스터 의 개발(또는 하위) 분기를 개발자 환경(통합)에 배포할 때 배포 스크립트는 Google Analytics을 비활성화합니다.

## 원인

이 기능은 개발자 데이터 및 상호 작용이 Google Analytics으로 전송되거나 추적되지 않도록 하기 위한 것입니다.

## 솔루션

Google Analytics을 항상 활성화하려면 개발자 설명서의 [변수 배포](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics)에 설명된 대로 배포 변수 `ENABLE_GOOGLE_ANALYTICS = true`을(를) 설정하십시오.

>[!NOTE]
>
>이 문서에는 일부 사람들이 인종차별주의자, 성차별주의자 또는 억압적이라고 생각할 수 있고 독자로 하여금 상처받거나, 트라우마를 받거나, 환영받지 못하게 만들 수 있는 업계 표준 소프트웨어 용어가 여전히 포함되어 있을 수 있다는 것을 알고 있습니다. Adobe은 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하고 있습니다.
