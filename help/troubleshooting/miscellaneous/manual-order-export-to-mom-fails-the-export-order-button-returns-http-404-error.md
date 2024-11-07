---
title: MOM으로 수동 주문 내보내기가 실패합니다. 순서 내보내기 단추를 누르면 HTTP 404 오류가 반환됩니다
description: 이 문서에서는 Commerce 관리자의 주문 보기에서 **주문 내보내기** 단추를 클릭하여 주문 Magento Order Management(MOM)을 내보내려고 하면 "*404 페이지를 찾을 수 없음*" 오류가 반환되는 문제를 해결하는 방법에 대해 설명합니다.
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# MOM으로 수동 주문 내보내기가 실패합니다. 순서 내보내기 단추를 누르면 HTTP 404 오류가 반환됩니다

이 문서에서는 Commerce 관리자의 주문 보기에서 **Magento Order Management 내보내기** 단추를 클릭하여 주문(MOM)을 내보내려고 하면 &quot;*404 페이지를 찾을 수 없음*&quot; 오류가 반환되는 문제를 해결하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.2.x, 2.3.x
* MOM 커넥터 2.3.0, 2.4.0, 3.2.0, 3.3.0

## 문제

<u>재현 단계:</u>:

1. Commerce 관리자에서 **판매 > 주문**&#x200B;을 클릭합니다.
1. **새 순서 만들기** 단추를 클릭합니다.
1. 사용자를 선택하고 항목을 추가하고 결제 및 배송 방법을 선택한 다음 **주문 제출** 단추를 클릭하십시오.
1. **순서 내보내기** 단추를 클릭한 다음 **확인**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

주문은 MOM에게 보내집니다.

<u>실제 결과</u>:

&quot; *404 오류: 페이지를 찾을 수 없음*&quot; 페이지가 표시됩니다.

## 솔루션

* Adobe Commerce 2.3.x의 경우 MOM 커넥터를 3.4.0으로, Adobe Commerce 2.2.x의 경우 MOM 커넥터 2.5로 업그레이드하십시오.
* MOM 커넥터 업그레이드가 옵션이 아닌 경우 CLI 명령을 사용하여 Magento Order Management 순서를 내보낼 수 있습니다.

```bash
$bin/magento oms:orders:sync
```

## 관련 읽기

[Magento Order Management 기술 설명서](https://commerce-docs.github.io/oms-documentation-archive/)
