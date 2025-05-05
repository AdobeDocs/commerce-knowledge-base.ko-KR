---
title: PHP 설정 오류
description: 이 문서에서는 PHP 설정 오류에 대한 해결책을 제공합니다.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# PHP 설정 오류

이 문서에서는 PHP 설정 오류에 대한 해결책을 제공합니다.

## PHP 메모리 제한 오류

준비 검사를 통해 PHP 프로세스에 1GB 이상의 메모리가 할당되어 있는지 확인합니다. 이 설정은 선택적 샘플 데이터 설치를 포함하여 대부분의 설치에 충분해야 합니다. 단, 디버깅에는 최소 2GB를 사용하는 것이 좋습니다.

PHP 메모리 제한을 늘리려면:

1. Adobe Commerce 서버에 로그인.
1. 다음 명령을 사용하여 `php.ini` 파일을 찾습니다.

   ```
   bash    $ php --ini
   ```

1. `root` 권한이 있는 사용자는 텍스트 편집기를 사용하여 `Loaded Configuration File`에서 지정한 `php.ini`을(를) 엽니다.
1. `memory_limit` 찾기.
1. 일반적인 사용 및 디버깅을 위해 값을 `2GB`(으)로 변경하십시오.
1. 변경 내용을 `php.ini`에 저장하고 텍스트 편집기를 종료합니다.
1. 웹 서버를 다시 시작합니다. 예제는 다음과 같습니다.

   * CentOS: `service httpd restart`
   * 우분투: `service apache2 restart`
   * nginx(CentOS 및 Ubuntu 모두): `service nginx restart`

1. 설치를 다시 시도하십시오.

## 큰 양식으로 인한 max-input-vars 오류

많은 스토뷰, 제품, 속성 또는 옵션이 있는 구성은 사전 설정된 PHP 제한을 초과하는 양식을 생성할 수 있습니다. 보낸 값 수가 `php.ini` 내에 설정된 `max-input-vars` 제한을 초과하는 경우(기본값 1,000) 나머지 데이터는 전송되지 않고 해당 데이터베이스 값이 업데이트되지 않습니다. 이 경우 PHP 로그에 경고가 나타납니다.

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

`max-input-vars`에 대한 &#39;적절한&#39; 값이 없습니다. 구성의 크기와 복잡성에 따라 다릅니다. 필요에 따라 `php.ini` 파일의 값을 수정합니다. [필수 PHP 설정](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/php-settings)을 참조하세요.

## xdebug 최대 함수 중첩 수준 오류

[설치하는 동안 xdebug 최대 함수 중첩 수준 오류](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md)를 참조하십시오.

## PHTML 템플릿에 액세스할 때 오류가 표시됩니다

오류 텍스트는 일반적으로 다음과 같습니다.

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### 해결 방법: php.ini에서 `asp_tags = off` 설정

제품 이미지를 표시하기 위해 [template](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml)과 같이 `<% %>` 태그로 래핑된 템플릿(Twig와 같은 다른 템플릿 엔진 사용)에 대한 지원 추상 수준에 대한 구문이 여러 템플릿에 있습니다.

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

[asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags)에 대한 추가 정보입니다.

`php.ini`을(를) 편집하고 `asp_tags = off`을(를) 설정합니다. 자세한 내용은 [필수 PHP 설정](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/php-settings)을 참조하세요.
