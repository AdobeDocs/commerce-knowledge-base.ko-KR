---
title: 업그레이드 호환성 도구 오류 문제 해결
description: 이 문서에서는 업그레이드 호환성 도구를 사용하는 동안 발생할 수 있는 오류에 대해 설명하고 도구를 성공적으로 실행할 수 있도록 이러한 오류를 해결하는 솔루션을 제공합니다.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 업그레이드 호환성 도구 오류 문제 해결

이 문서에서는 업그레이드 호환성 도구를 사용하는 동안 발생할 수 있는 오류에 대해 설명하고 도구를 성공적으로 실행할 수 있도록 이러한 오류를 해결하는 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* [호환성 업그레이드 도구](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html)이(가) 2.3.0 이상에서 Adobe Commerce 버전과 호환됩니다.

## 세분화 오류

<u>원인</u>:

두 모듈의 이름이 같은 경우 업그레이드 호환성 도구에 세그멘테이션 오류 오류가 표시됩니다.

<u>솔루션</u>:

이 오류를 방지하려면 모듈의 경로를 인수로 지정하는 것이 좋습니다.

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> 업그레이드 호환성 도구는 메서드 간 순환 종속성이 포함된 경우 코드 베이스를 분석하지 못할 수 있습니다.

## 빈 출력

<u>재현 단계</u>:

1. 이 명령을 실행한 후 다음과 같은 경우:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. 출력만 `Upgrade compatibility tool`입니다.

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>원인</u>:

가능한 원인은 PHP 메모리 제한입니다.

이 PHP 메모리 제한을 피하기 위한 두 가지 가능한 해결책이 있습니다.

<u>솔루션 1</u>:

`memory_limit`을(를) `-1`(으)로 설정하여 메모리 제한을 재정의합니다.

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> `M2_VERSION`은(는) Adobe Commerce 인스턴스와 비교할 대상 Adobe Commerce 버전입니다.

<u>솔루션 2</u>:

`-m` 옵션을 추가하면 업그레이드 호환성 도구에서 각 특정 모듈을 독립적으로 분석하여 Adobe Commerce 인스턴스에서 이름이 같은 두 모듈이 발생하지 않도록 할 수 있습니다.

또한 이 명령 옵션을 사용하면 업그레이드 호환성 도구에서 여러 모듈이 포함된 폴더를 분석할 수 있습니다.

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

명령줄 인터페이스 옵션에 대한 자세한 내용은 [명령줄 인터페이스에서 도구 실행](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) 페이지를 참조하십시오.
