---
title: 설치 중, PHP 날짜 경고
description: 이 문서에서는 설치 중 PHP 날짜 경고에 대한 수정 사항을 제공합니다.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 1%
---
# 설치 중, PHP 날짜 경고

이 문서에서는 설치 중 PHP 날짜 경고에 대한 수정 사항을 제공합니다.

## 세부 사항 {#details}

설치하는 동안 다음 메시지가 표시됩니다.

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### 솔루션 {#solution}

PHP 시간대 설정을 주의 깊게 확인하십시오. 개발자 설명서에서 [설치 안내서 > PHP 설정](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/php-settings)을 참조하십시오.
