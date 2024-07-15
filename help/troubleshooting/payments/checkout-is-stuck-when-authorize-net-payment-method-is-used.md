---
title: Authorize.net 결제 방법을 사용하면 체크아웃이 중단됩니다.
description: 이 문서에서는 브라우저 콘솔 로그에 *'null의 속성 '길이'를 읽을 수 없음'* 오류 메시지와 함께 Authorize.net을 사용하는 경우 체크아웃이 중단되는 Adobe Commerce 2.3.X 문제에 대한 설명 및 수정 사항을 제공합니다.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Authorize.net 결제 방법을 사용하면 체크아웃이 중단됩니다.

이 문서에서는 Authorize.net을 사용하는 경우 체크아웃이 중단되는 Adobe Commerce 2.3.X 문제에 대한 설명과 수정 사항을 제공합니다. 브라우저 콘솔 로그에 *&#39;null의 &#39;length&#39; 속성을 읽을 수 없음&#39;* 오류 메시지가 표시됩니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.3.X

>[!NOTE]
>
>핵심 Adobe Commerce Authorize.Net 결제 통합은 2.3.4부터 더 이상 사용되지 않으며 2.4.0에서 완전히 제거되었습니다. 대신 [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/)의 요구 사항에 맞는 확장을 사용하십시오.

## 문제

<u>재현 단계</u>

1. Commerce 관리자에서 Authorize.net 결제 방법을 구성합니다.
1. 가게 앞쪽으로 가보세요
1. 장바구니에 제품을 추가하고 체크아웃을 진행합니다.
1. 결제 방법으로 Authorize.net 을 선택합니다.
1. **주문**&#x200B;을 클릭하세요.

<u>예상 결과</u>

Authorize.net iframe이 로드됩니다.

<u>실제 결과</u>

Ajax 회전자가 표시되고 페이지가 로드되지 않습니다. 다음 JS 오류가 브라우저 콘솔 로그에 표시됩니다. *&#39;Uncatch TypeError: b(jstest.authorize.net/v1/AcceptCore.js:1)&#39;*)에서 null의 &#39;length&#39; 속성을 읽을 수 없습니다.

## 원인

이 문제에 대한 가장 일반적인 이유 중 하나는 Commerce 관리자의 Authorize.Net 구성에 공개 클라이언트 키가 지정되지 않았기 때문입니다.

## 솔루션

**스토어** > **설정** > **구성** > **판매** > **결제 방법**&#x200B;에서 **Authorize.net** 섹션의 **공용 클라이언트 키** 필드에 값이 지정되어 있는지 확인하십시오. 비어 있는 경우 Authorize.Net 판매자 계정의 키 값을 입력합니다.

변경 사항을 적용하려면 를 실행하여 캐시를 정리합니다.

```bash
bin/magento cache:clean
```
