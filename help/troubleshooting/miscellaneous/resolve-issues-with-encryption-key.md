---
title: 암호화 키 관련 문제 해결
description: 이 문서에서는 암호화 키가 DB 덤프와 함께 다른 환경으로 이동되지 않아 발생하는 문제를 해결하는 방법에 대해 설명합니다.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 암호화 키 관련 문제 해결

이 문서에서는 암호화 키가 DB 덤프와 함께 다른 환경으로 이동되지 않아 발생하는 문제를 해결하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.x

## 문제

프로덕션에서 스테이징/통합 환경으로 [데이터베이스 덤프](/help/how-to/general/create-database-dump-on-cloud.md)를 가져온 후 저장된 신용 카드 번호가 잘못되었거나 판매자 자격 증명을 사용해야 하는 결제 통합에 대해 결제가 실패합니다.

## 원인

신용 카드 번호 및 판매자 자격 증명과 같은 중요한 데이터를 암호화하는 데 사용되는 암호화 키는 데이터베이스에 저장되지 않으므로 데이터베이스 덤프 가져오기/내보내기 후 다른 환경으로 전송되지 않습니다.

## 솔루션

소스 환경에서 암호화 키를 복사하여 대상 환경에 추가해야 합니다.

암호화 키를 복사하려면:

1. 개발자 설명서의 [환경에 대한 SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=ko)에 설명된 대로 데이터베이스 덤프의 소스인 프로젝트에 대한 SSH입니다.
1. 텍스트 편집기에서 `app/etc/env.php` 열기
1. `crypt`의 `key` 값을 복사합니다.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

대상 프로젝트에 대한 키 값을 설정하려면 다음을 수행합니다.

1. [클라우드 콘솔](https://console.adobecommerce.com)을 열고 프로젝트를 찾습니다.
1. 개발자 설명서에서 [프로젝트 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=ko)에 설명된 대로 [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko)(개발자 설명서에서) 변수의 값을 설정합니다. 이렇게 하면 배포 프로세스가 트리거되고 모든 배포의 `app/etc/env.php` 파일에서 `CRYPT_KEY`이(가) 재정의됩니다.

선택적으로 `app/etc/env.php` 파일의 암호화 키를 수동으로 재정의할 수 있습니다.

1. 대상 환경에 SSH를 추가합니다.
1. 텍스트 편집기에서 `app/etc/env.php` 열기
1. 복사한 데이터를 `crypt`의 `key` 값으로 붙여 넣습니다.
1. 편집된 `env.php`을(를) 저장합니다.
1. `bin/magento cache:clean`을(를) 실행하거나 **시스템** > **도구** > **캐시 관리**&#x200B;의 Commerce 관리에서 대상 환경의 캐시를 정리합니다.
