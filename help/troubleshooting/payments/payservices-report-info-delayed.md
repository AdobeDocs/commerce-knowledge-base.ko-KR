---
title: 지연 결제 서비스 보고서 데이터
description: 이 문서에서는 결제 서비스의 보고 데이터가 지연될 수 있는 이유를 설명합니다.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 지연 결제 서비스 보고서 데이터

이 문서에서는 결제 서비스의 보고 데이터가 지연될 수 있는 이유를 설명합니다.

## 영향을 받는 제품 및 버전

* [결제 서비스](https://marketplace.magento.com/magento-payment-services.html)가 이제 Adobe Commerce 버전 2.4.0에서 2.4.4로 호환됩니다.

## 문제

결제 및 주문 결제 상태 보고서에 대한 결제 서비스 보고 데이터가 즉시 동기화되지 않을 수 있습니다.

예를 들어 주문의 송장 발행(캡처)이나 주문에 대한 대변 메모 발행 후 주문 상태를 즉시 사용할 수 없습니다.

<u>재현 단계</u>:

전제 조건: 주문은 결제 서비스 기능을 사용하여 수행됩니다.

1. [관리자](https://docs.magento.com/user-guide/stores/admin.html)의 주문은 [인보이스가 청구됨](https://docs.magento.com/user-guide/sales/invoice-create.html)(또는 [취소됨](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) 또는 [대변 메모를 통해 환불됨](https://docs.magento.com/user-guide/sales/credit-memos.html))입니다.
1. 해당 주문에 대한 정보를 보려면 주문 지급 상태 보고서로 이동합니다.
1. 상태가 `AUTHORIZED`(으)로 표시됩니다. 이 상태는 송장 발행 또는 기타 주문 조치 이전의 주문 상태입니다.

   Commerce은 데이터를 동기화하지 않고 결제 서비스로 보냈으므로 보고서에서 새 주문 상태를 아직 인식하지 못합니다.

>[!NOTE]
>
>이는 하나의 일반적인 사용 사례일 뿐입니다. [주문 작업](https://docs.magento.com/user-guide/sales/order-actions.html)이 발생하고 해당 보고서에서 데이터를 즉시 사용할 수 없는 다른 사용 사례가 있을 수 있습니다.

<u>예상 결과</u>:
보고서 데이터는 주문에 대한 작업이 있는 즉시 채워집니다.

<u>실제 결과</u>:
방금 완료한 주문 작업에 대한 보고서 데이터가 지연될 수 있습니다. 지급 보고서는 24~48시간의 지연을 발생시킬 수 있습니다. 주문 결제 상태 보고서는 몇 시간 정도 지연될 수 있습니다.

## 원인

관리자의 표시되는 데이터의 이러한 지연에 영향을 주는 두 가지 요소가 있습니다.

* Admin의 [구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html)을 통해 Commerce에서 데이터를 동기화(내보내기 및 유지)하도록 선택하는 빈도입니다.
* PayPal이 보고 데이터를 게시하는 일정.

## 솔루션

주문 결제 상태 보고서의 경우:

1. **판매** > **결제 서비스**(으)로 이동합니다.
1. 주문 결제 상태 보고서 테이블을 보려면 **주문 결제 상태**&#x200B;를 클릭하십시오.
1. 보고서 테이블의 오른쪽 상단에 있는 **강제 재동기화** 아이콘을 클릭하여 강제 재동기화합니다.
1. 마지막으로 업데이트된 타임스탬프 변경 사항과 보고서 테이블에 로드된 새 트랜잭션이 표시됩니다.

PayPal 페이아웃 보고서의 경우 예상 결과는 PayPal의 데이터 게시 일정에 대한 종속성으로 인해 24-48h의 지연입니다.
