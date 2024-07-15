---
title: 'Adobe Commerce 2.4.0 문제: storefront 원시 메시지 데이터 표시'
description: 이 문서에서는 상점 첫 화면의 모든 오류 메시지에 공백이 아닌 "+" 기호가 표시되었을 때 발생하는 문제에 대한 해결 방법을 제공합니다. 이 솔루션은 오류 메시지를 계속 읽을 수 있도록 도와줍니다.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 문제: storefront raw 메시지 데이터 표시

이 문서에서는 상점 첫 화면의 모든 오류 메시지에 공백이 아닌 &quot;+&quot; 기호가 표시되었을 때 발생하는 문제에 대한 해결 방법을 제공합니다. 이 솔루션은 오류 메시지를 계속 읽을 수 있도록 도와줍니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0.

## 문제

<u>재현 단계:</u>

1. 상점 첫 화면의 **새 계정 만들기** 페이지로 이동합니다.
1. 등록된 이메일을 사용하여 새 계정을 만듭니다. 다음 메시지가 표시됩니다.

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## 원인

이 문제는 set\\read 쿠키와 관련된 PHP 7.4.2 문제로 인해 발생합니다. [PHP BUG \#79174 setcookie() 는 공백을 \`+\`로 인코딩하지만 $\_COOKIE는 더 이상 디코딩하지 않습니다](https://bugs.php.net/bug.php?id=79174).

## 솔루션

이 문제를 해결하려면 PHP 7.4.x의 다른 버전을 사용하십시오. PHP 7.4.2는 Adobe Commerce 2.4.0에서 지원되지 않습니다.

## 지원 기술 자료의 관련 자료:

* [Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0의 배송 라벨 작성 알려진 문제](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0 알려진 문제: 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
