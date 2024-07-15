---
title: 2.3.4 PayPal 문제 핫픽스
description: 이 문서에서는 PayPal Express Checkout에서 영역을 선택할 때 주문 배치 중에 발생하는 오류에 대한 수정 사항을 제공합니다. 이 문제는 Adobe Commerce v2.3.4 릴리스의 변경 사항으로 인해 발생하며 PayPal Express 체크아웃 주소 필드를 구문 분석하는 방법과 관련이 있습니다.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 PayPal 문제 핫픽스

이 문서에서는 PayPal Express Checkout에서 영역을 선택할 때 주문 배치 중에 발생하는 오류에 대한 수정 사항을 제공합니다. 이 문제는 Adobe Commerce v2.3.4 릴리스의 변경 사항으로 인해 발생하며 PayPal Express 체크아웃 주소 필드를 구문 분석하는 방법과 관련이 있습니다.

## 영향을 받는 버전 및 제품

* 클라우드 인프라의 Adobe Commerce v2.3.4
* Adobe Commerce 온-프레미스 v2.3.4

## 문제

PayPal Express Checkout에서 주문을 넣는 동안 해당 국가 및 지역을 입력할 때 오류가 발생합니다. 이 문제는 주소 섹션의 지역 필드가 텍스트 필드인 모든 국가에서 재현할 수 있습니다(드롭다운 메뉴와 반대).

<u>재현 단계</u>:

1. PayPal Express 체크아웃을 활성화합니다.
1. 장바구니에 제품을 게스트로 추가하거나 로그인했을 때 추가합니다.
1. 체크아웃으로 이동합니다.
1. 배송 주소를 선택하십시오. 예: *UK* . **시/도** 필드에 입력을 입력하십시오. 예를들어 *Nottinghamshire*&#x200B;입니다.
1. 주문하려면 **주문** 단추를 클릭하십시오. 성공적인 주문 페이지와 주문 확인 이메일을 받게 됩니다.

<u>예상 결과:</u>

주문이 성공적으로 완료되었습니다.

<u>실제 결과:</u>

주문 버튼을 클릭하면 다음 오류가 표시됩니다.

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## 솔루션

Adobe Commerce 온-프레미스 판매자의 경우: 내 계정의 [magento.com](https://magento.com) 포털의 다운로드 섹션에서 사용할 수 있는 [핫픽스,](https://magento.com/tech-resources/download#download2353)을(를) 적용합니다.

클라우드 인프라 판매자의 Adobe Commerce: Adobe이 Commerce v1.0.2용 클라우드 패치에 수정 사항을 포함했습니다. 최신 패키지 적용에 대한 지침은 개발자 설명서에서 [Commerce용 클라우드 패치](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche)를 참조하십시오.

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 관련 읽기

* [릴리스 정보 > Adobe Commerce 2.3.4 릴리스 노트 > Adobe Commerce 2.3.4용 지역 패치와 함께 PayPal Express 체크아웃 문제 적용](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) 개발자 설명서에서 중요한 PayPal Express 체크아웃 문제를 해결하십시오.
