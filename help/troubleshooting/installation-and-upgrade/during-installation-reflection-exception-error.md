---
title: 설치하는 동안 반사 예외 오류가 발생했습니다.
description: 이 문서에서는 설치 중 발생하는 반사 예외 오류에 대한 해결 방법을 제공합니다.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '96'
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

Adobe Commerce에서 모든 디렉터리 및 파일 지우기 `var` 하위 디렉터리와 Adobe Commerce 소프트웨어를 다시 설치합니다.

다음으로: [Adobe Commerce 파일 시스템 소유자](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) 또는 을 사용하는 사용자로 `root` 권한, 다음 명령을 입력합니다.

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
