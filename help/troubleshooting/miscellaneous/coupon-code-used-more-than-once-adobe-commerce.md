---
title: 단일 사용을 위한 쿠폰은 여러 번 사용됨, Adobe Commerce
description: 이 문서에서는 장바구니 가격 규칙 쿠폰이 제대로 작동하지 않는 문제에 대한 해결 방법을 제공합니다. 가맹점은 1회용 쿠폰을 설정해 고객이 여러 번 사용할 수 있다.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# 단일 사용을 위한 쿠폰은 여러 번 사용됨, Adobe Commerce

이 문서에서는 장바구니 가격 규칙 쿠폰이 제대로 작동하지 않는 문제에 대한 해결 방법을 제공합니다. 가맹점은 1회용 쿠폰을 설정해 고객이 여러 번 사용할 수 있다.


## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 방법) 2.4.3 이상

## 문제

가맹점은 1회용 쿠폰을 설정해 고객이 여러 번 사용할 수 있다.

<u>재현 단계</u>:

1. 쿠폰을 만들고 한 번 사용하도록 쿠폰을 구성합니다.
1. 체크아웃을 진행합니다.
1. 방금 생성한 쿠폰을 사용합니다.
1. 체크아웃을 다시 진행하고 같은 쿠폰을 쓰세요.

<u>예상 결과</u>:

쿠폰은 한 번만 사용 가능합니다. 메시지가 표시됩니다. *쿠폰 코드 &quot;COUPON_NAME&quot;은 유효하지 않습니다.*.

<u>실제 결과</u>:

쿠폰은 한 번 이상 사용할 수 있습니다.


## 원인

상인은 이(가) 없습니다 `sales.rule.update.coupon.usage` 소비자가 이를 설정하고 실행하면 부적절한 동작이 발생합니다.

## 솔루션

추가 `sales.rule.update.coupon.usage` 소비자 대상 `app/etc/env.php` 파일.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

자세한 단계는 를 참조하십시오. [메시지 대기열 관리 > 구성](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html#configuration) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

[메시지 대기열 개요](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html) 개발자 설명서에서 확인할 수 있습니다.
