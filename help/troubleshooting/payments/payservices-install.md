---
title: 결제 서비스 설치 문제 해결
description: 이 문서에서는 결제 서비스 설치 시 발생할 수 있는 오류에 대해 설명하고 설치를 완료할 수 있도록 이러한 오류를 수정하는 방법을 제공합니다.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# 결제 서비스 설치 문제 해결

이 문서에서는 결제 서비스 설치 시 발생할 수 있는 오류에 대해 설명하고 설치를 완료할 수 있도록 이러한 오류를 수정하는 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* [결제 서비스](https://marketplace.magento.com/magento-payment-services.html) 는 이제 Adobe Commerce 버전 2.4.0에서 2.4.4로 호환됩니다.

## 문제 - 잘못된 작성기 키

결제 서비스 확장을 설치할 때 설치 중에 잘못된 작성기 키를 사용했다는 오류 메시지가 표시될 수 있습니다.

<u>재현 단계</u>:

1. 시도 [결제 서비스 설치](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. 다음 오류를 참조하십시오.

   *패키지 magento/payment-services와 일치하는 버전을 찾을 수 없습니다. 패키지 철자, 버전 제약 조건 및 패키지가 최소 안정성과 일치하는 안정성으로 사용 가능한지 확인합니다(안정적).*

<u>예상 결과</u>:

다음 단계를 따를 수 있습니다. [설치 지침](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) 개발자 설명서에서 결제 서비스를 성공적으로 설치하십시오.

<u>실제 결과</u>:

설치하는 동안 올바른 Composer 키를 사용하지 않았다는 오류 메시지가 표시됩니다.

### 원인

설치하는 동안 잘못된 Composer 키를 사용했습니다.

### 솔루션

다음을 확인합니다. [작성기 키가 Magento ID에 연결되어 있습니다.](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#incorrect-composer-keys) 결제 서비스 등록 중에 사용됩니다.

## 문제 - 여러 인스턴스에서 동일한 데이터 공간 사용

각각에 대해 결제 서비스를 사용하여 다중 환경 설정을 실행합니다.

### 솔루션

인스턴스 간에 동일한 API 키를 사용할 수 있지만 각 인스턴스는 자체 SaaS 데이터 공간을 사용해야 합니다.

SaaS 프로젝트를 만들 때 Commerce은 Commerce 라이선스에 따라 하나 이상의 SaaS 데이터 공간을 생성합니다.

* Adobe Commerce - 프로덕션 데이터 공간 1개, 테스트 데이터 공간 2개
* Magento Open Source - 프로덕션 데이터 공간 1개, 테스트 데이터 공간 없음

의 지침을 따르십시오. [Commerce API 키 및 개인 키](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#obtain-api-credentials) 결제 서비스 확장을 구성했습니다.

## 문제 - 메모리가 부족하여 PHP를 할 수 없습니다.

결제 서비스 확장을 설치하면 PHP에 사용할 메모리가 부족하다는 오류 메시지가 표시될 수 있습니다.

<u>재현 단계</u>:

1. 시도 [결제 서비스 설치](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. 다음 오류 또는 유사한 오류를 참조하십시오.

   *치명적 오류: 52행의 phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php에서 2146435072바이트의 허용된 메모리 크기가 소진되었습니다(4096바이트 할당 시도).*

<u>예상 결과</u>:

다음 단계를 따를 수 있습니다. [설치 지침](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) 개발자 설명서에서 결제 서비스를 성공적으로 설치하십시오.

<u>실제 결과</u>:

설치 중에 PHP에 필요한 메모리가 부족하다는 오류 메시지가 표시됩니다.

### 원인

환경에서 PHP에 대한 제한이 충분히 높은 임계값으로 설정되어 있지 않습니다.

### 솔루션

[PHP에 대한 메모리 제한 늘이기](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#not-enough-memory-for-php) 의 환경에서 `php.ini`.
