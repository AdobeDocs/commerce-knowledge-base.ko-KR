---
title: '''Magento-cloud'' [!DNL CLI]에 활성 환경이 표시되지 않음'
description: 이 문서에서는 'Magento-cloud' [!DNL CLI](명령줄 도구)에 활성 환경이 표시되지 않는 알려진 Adobe Commerce 문제에 대해 설명합니다.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%
---
# `Magento-cloud` [!DNL CLI]에 활성 환경이 표시되지 않습니다.

## 문제

몇 가지 활성 환경이 있으며 `Magento-cloud` [!DNL CLI]&#x200B;(명령줄 도구) 명령을 실행하여 환경과 상호 작용하려고 합니다. (예: `ssh`, `db:size`, `db:sql` 등)
그러나 원하는 환경을 선택하라는 메시지가 이 환경을 나열하지 않습니다. (예: 통합 환경)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## 원인

배포 진행 중, 중단 또는 실패로 인해 환경을 사용할 수 없습니다.

## 솔루션

`e|-environment` 플래그를 사용하여 환경을 수동으로 지정해야 합니다.

1. 활성 환경 목록을 찾고 환경 이름을 기록합니다.

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

&#x200B;2. 명령을 사용하여 환경 ID를 지정합니다.

`magento-cloud ssh -e integration`
