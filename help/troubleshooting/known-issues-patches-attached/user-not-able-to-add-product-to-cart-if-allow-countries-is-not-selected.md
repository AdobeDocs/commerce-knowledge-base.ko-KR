---
title: 허용 국가에서 아무것도 선택하지 않은 경우 사용자가 제품을 장바구니에 추가할 수 없음
description: 이 문서에서는 국가 허용 을 선택하지 않은 경우 사용자가 제품을 장바구니에 추가할 수 없는 알려진 Adobe Commerce 2.4.4(PHP 8.1 포함) 문제에 대한 패치를 제공합니다.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# 허용 국가에서 아무것도 선택하지 않은 경우 사용자가 제품을 장바구니에 추가할 수 없음

이 문서에서는 국가 허용 을 선택하지 않은 경우 사용자가 제품을 장바구니에 추가할 수 없는 알려진 Adobe Commerce 2.4.4(PHP 8.1 포함) 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce 2.4.4(PHP 8.1 포함)

## 문제

국가 허용 을 선택하지 않으면 사용자가 제품을 장바구니에 추가할 수 없습니다.

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다.
1. **스토어** > **구성** > **일반** > **국가 옵션**(으)로 이동
1. **국가 허용** 필드에서 모든 옵션을 선택 취소합니다.
1. 구성을 저장하려면 **구성 저장**&#x200B;을 클릭하세요.
1. 상점으로 이동하여 장바구니에 제품을 추가해 보십시오.

<u>예상 결과:</u>

장바구니에 제품을 추가할 수 있습니다.

<u>실제 결과:</u>

장바구니에 제품을 추가할 수 없습니다. 다음과 같은 콘솔 오류가 발생합니다.

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## 원인

다중 선택 구성에 선택한 항목이 없는 경우 Adobe Commerce 구성은 `null`을(를) 검색합니다. 이 구성은 8.1 이전 버전의 PHP에서 성공적으로 처리된 경우. 그러나 PHP 8.1에서는 &quot;[PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;에서 Null을 허용하지 않는 내부 함수의 인수에 Null을 전달하는 것을 사용하지 마십시오.

## 솔루션

이 문제를 해결하려면 다음 패치를 적용합니다.

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## 패치 적용 방법

자세한 내용은 지원 기술 자료에서 [Adobe Commerce에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 유용한 링크

개발자 설명서에서 [클라우드 인프라의 Adobe Commerce에 사용자 지정 패치를 적용](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)합니다.
