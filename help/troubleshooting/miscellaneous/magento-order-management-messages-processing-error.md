---
title: Adobe Commerce 처리 오류에 대한 OMS(Magento Order Management 시스템)
description: 이 문서에서는 Adobe Commerce용 Magento Order Management 시스템(OMS)에서 'bin/magento oms:messages:process'를 실행하는 CLI에서 'getMode()' 오류가 발생하는 문제에 대한 해결 방법을 제공합니다.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Adobe Commerce 처리 오류에 대한 OMS(Magento Order Management 시스템)

이 문서에서는 Adobe Commerce용 Magento Order Management 시스템(OMS)에서 `bin/magento oms:messages:process`을(를) 실행하는 CLI에서 `getMode()` 오류가 발생하는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

이 오류는 MCOM 커넥터 릴리스 3.1.1 및 3.2.0을 사용할 때 발생합니다. MCOM 커넥터 3.3.0에서 해결되었습니다. MDC 또는 MOM 버전에만 적용되는 것은 아닙니다.

## 문제

CLI에서 다음 명령을 실행할 때:

`bin/magento oms:messages:process`

다음과 유사한 오류 메시지가 CLI에 출력됩니다.

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## 원인

E
이 문제는 커넥터가 `magento.inventory.source_management`개 메시지를 처리하려고 할 때 발생합니다. 커넥터는 이러한 메시지를 모드 값이 필요한 `magento.inventory.source_stock_management.update` 메시지인 것처럼 처리하려고 합니다. `magento.inventory.source_mangement` 메시지에 모드가 없으므로 오류가 발생합니다.

## 솔루션

이 문제를 해결하려면 CLI에서 다음 [!DNL SQL] 문을 실행하여 `mcom_api_messages` 테이블의 모든 레코드를 삭제합니다.

`delete from mcom_api_messages;`

## 관련 읽기

* OMS 문서 [OMS 커넥터 설정 자습서](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
