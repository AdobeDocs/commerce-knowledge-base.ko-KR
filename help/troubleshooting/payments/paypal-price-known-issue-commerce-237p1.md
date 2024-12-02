---
title: 'Adobe Commerce 2.3.7-p1의 알려진 문제: PayPal에 대한 이전 주문 총계'
description: 이 문서에서는 Adobe Commerce 2.3.7-p1의 알려진 문제에 대한 패치를 제공합니다. PayPal Checkout을 두 번 이상 사용하면 고객이 주문하려는 새 제품 대신 장바구니에서 이전에 주문한 제품을 받을 수 있습니다.
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Adobe Commerce 2.3.7-p1의 알려진 문제: PayPal에 대한 이전 주문 총계

이 문서에서는 Adobe Commerce 2.3.7-p1의 알려진 문제에 대한 패치를 제공합니다. PayPal Checkout을 두 번 이상 사용하면 고객이 주문하려는 새 제품 대신 장바구니에서 이전에 주문한 제품을 받을 수 있습니다.
이 문서에서 패치를 다운로드할 수 있으며 Quality Patches Tool(QPT)을 통해서도 사용할 수 있습니다.

## 영향을 받는 버전

* Adobe Commerce (모든 배포 옵션) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## 문제

PayPal Express Checkout 결제 방법을 사용하여 주문하면 이전에 주문한 구매 제품이 실제 제품이 아닌 주문에 추가됩니다.

<u>재현 단계:</u>

1. 매장 앞쪽에서 장바구니에 제품을 추가합니다(제품 A, 가격 $50).
1. 장바구니 링크를 클릭하여 장바구니를 엽니다.
1. **PayPal 체크아웃** 단추를 클릭합니다.
1. PayPal 자격 증명을 사용하여 PayPal에 로그인하고 결제를 제출합니다.
1. 스토어 측의 주문 배치를 완료합니다.
1. 카탈로그로 돌아가서 다른 제품(제품 B, 가격 $100)을 장바구니에 추가하십시오.
1. 장바구니 링크를 클릭하여 장바구니를 엽니다.
1. **PayPal 체크아웃** 단추를 클릭합니다.

<u>실제 결과:</u>

장바구니에 있는 제품 가격은 $100가 아닌 $50입니다.<br/>
매장 측 주문서에는 B제품 대신 A제품이 포함되어 있습니다.

<u>예상 결과:</u>

B 제품이 주문에 추가됩니다.

## 솔루션

이 문서에 제공된 패치를 적용합니다.

## 패치

다음 링크를 사용하여 패치가 포함된 .zip 파일을 다운로드합니다. [MC42674-composer.patch.zip](assets/MC42674-composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전

* Adobe Commerce (모든 배포 옵션) 2.3.7-p1

## 패치 적용 방법

1. 다운로드한 .zip 파일의 압축을 해제합니다.
1. 자세한 지침은 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.
