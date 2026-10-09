---
title: 설치하는 동안 반사 예외 오류가 발생했습니다.
description: 이 문서에서는 설치 중 발생하는 반사 예외 오류에 대한 해결 방법을 제공합니다.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
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
source-wordcount: '107'
ht-degree: 0%
---
# 설치하는 동안 반사 예외 오류가 발생했습니다.

이 문서에서는 설치 중 발생하는 반사 예외 오류에 대한 해결 방법을 제공합니다.

## 세부 사항 {#details}

설치하는 동안 다음과 유사한 메시지가 표시됩니다.

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## 솔루션 {#solution}

Adobe Commerce의 `var` 하위 디렉터리에서 모든 디렉터리와 파일을 지우고 Adobe Commerce 소프트웨어를 다시 설치하십시오.

[Adobe Commerce 파일 시스템 소유자](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) 또는 `root` 권한이 있는 사용자로 다음 명령을 입력하십시오.

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### 레디스 {#redis}

Redis를 사용해도 오류가 발생하면 다음과 같이 Redis 캐시를 지웁니다.

```bash
$ redis-cli FLUSHALL
```
