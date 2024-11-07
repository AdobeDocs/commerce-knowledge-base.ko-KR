---
title: 작성기의 변경 사항으로 인해 다운로드가 실패합니다.
description: 이 문서에서는 실패한 Adobe Commerce 다운로드 및 예외 오류에 대한 수정 사항을 제공합니다.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# 작성기의 변경 사항으로 인해 다운로드가 실패합니다.

이 문서에서는 실패한 Adobe Commerce 다운로드 및 예외 오류에 대한 수정 사항을 제공합니다.

## 문제

다운로드하는 동안 다음 오류가 표시됩니다.

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## 원인

이 문제는 특정 버전의 Composer가 변경되었기 때문에 발생합니다. 해결 방법은 Composer를 이전 버전으로 다운그레이드하고 Adobe Commerce 다운로드를 다시 시도하는 것입니다.

## 솔루션

2015년 11월 21일부터 11월 26일 사이의 모든 Composer 버전에는 이 문제가 있습니다. 이 문제가 Composer 버전과 관련이 있는지 확인하려면 다음 명령을 입력합니다.

```php
composer -v
```

버전은 다음과 유사하게 표시됩니다.

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

날짜가 2015-11-25입니다. 이는 Composer에 이 문제가 있음을 나타냅니다.

해결 방법:

1. 다음 중 하나를 수행하여 Adobe Commerce 소프트웨어를 다운로드할 수 있도록 Composer 버전을 변경합니다.

   * `composer self-update 1.0.0-alpha11` 명령을 사용하여 Composer를 다운그레이드합니다.
   * Composer를 2015년 11월 26일 이후의 버전으로 업그레이드하십시오. `composer self-update`.

1. Adobe Commerce 디렉터리 및 하위 디렉터리를 삭제합니다.
1. `[composer create-project](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer)` 또는 `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`을(를) 사용하여 다운로드를 다시 시도하십시오.
1. Adobe Commerce 소프트웨어를 성공적으로 다운로드한 후 작성기 `composer self-update`을(를) 업데이트합니다.
