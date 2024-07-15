---
title: 설치 중, PHP 날짜 경고
description: 이 문서에서는 설치 중 PHP 날짜 경고에 대한 수정 사항을 제공합니다.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# 설치 중, PHP 날짜 경고

이 문서에서는 설치 중 PHP 날짜 경고에 대한 수정 사항을 제공합니다.

## 세부 사항 {#details}

설치하는 동안 다음 메시지가 표시됩니다.

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### 솔루션 {#solution}

PHP 시간대 설정을 주의 깊게 확인하십시오. 개발자 설명서에서 [설치 안내서 > PHP 설정](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)을 참조하십시오.
