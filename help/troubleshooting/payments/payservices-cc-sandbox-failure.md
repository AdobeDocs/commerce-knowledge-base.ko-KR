---
title: 샌드박스 환경에서 신용카드 결제 실패
description: 이 문서에서는 PayPal API를 사용하는 샌드박스 환경에서 테스트 신용카드가 실패한 이유를 설명합니다.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 샌드박스 환경에서 신용카드 결제 실패

이 문서에서는 PayPal API를 사용하는 샌드박스 환경에서 테스트 신용카드가 실패한 이유를 설명합니다.

## 영향을 받는 제품 및 버전


* Adobe Commerce 2.4.0 - 2.4.4 , 모든 배포 옵션, [결제 서비스](https://marketplace.magento.com/magento-payment-services.html)

## 문제

테스트 비자 신용 카드를 사용할 때 `4111 1111 1111 1111` payPal에서 다음과 같은 오류로 인해 PayPal 사기 정책으로 인해 실패하는 경우가 있습니다.

```terminal
Error happened when processing the request. Please try again later.
```

## 원인

이 오류는 PayPal이 사기에 대한 특정 테스트 신용 카드 번호에 플래그를 지정할 때 표시됩니다. 이는 PayPal API로 테스트하는 전 세계 모든 사용자가 사용하는 테스트 신용 카드 번호이기 때문에 발생합니다.

## 솔루션

다른 테스트 신용 카드를 사용하십시오. 테스트에 사용할 수 있는 모의 신용 카드를 생성하려면:

1. PayPal 개발자 포털로 이동 [신용 카드 생성기](https://developer.paypal.com/developer/creditCardGenerator/) 페이지를 가리키도록 업데이트하는 중입니다.
1. PayPal 개발자 포털 대시보드에 로그인합니다.
1. 테스트 신용 카드를 생성합니다.
