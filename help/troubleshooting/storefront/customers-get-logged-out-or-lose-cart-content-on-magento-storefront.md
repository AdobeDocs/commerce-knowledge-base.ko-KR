---
title: 고객이 Adobe Commerce 상점 첫 화면에서 로그아웃되거나 장바구니 콘텐츠가 손실됨
description: 이 문서에서는 고객이 결제 또는 기타 타사 서비스에서 Adobe Commerce 스토어로 다시 이동한 후(세션 쿠키가 "손실됨") 스토어프런트의 장바구니에서 로그아웃되거나 항목을 잃는 문제에 대한 해결 방법과 해결 방법을 제공합니다.
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%
---
# 고객이 Adobe Commerce 상점 첫 화면에서 로그아웃되거나 장바구니 콘텐츠가 손실됨

이 문서에서는 고객이 결제 또는 기타 타사 서비스에서 Adobe Commerce 스토어로 다시 이동한 후(세션 쿠키가 &quot;손실됨&quot;) 상점 앞의 장바구니에서 로그아웃되거나 항목을 잃는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

<u>재현 단계:</u>

1. 고객이 상점 앞의 장바구니에 제품을 추가하고 체크아웃을 진행합니다.
1. 고객은 결제/배송 또는 기타 정보/서비스를 위해 서드파티 사이트로 리디렉션됩니다.
1. 고객이 다시 상점으로 리디렉션됩니다.

<u>실제 결과:</u>

고객이 빈 장바구니 또는 빈 페이지로 리디렉션되었습니다.

<u>예상 결과:</u>

고객이 체크아웃 데이터와 진행 상황을 손실하지 않고 성공 결제 페이지(또는 기타 성공 페이지)로 리디렉션했습니다.

## 원인

SameSite 쿠키 특성이 *Lax*(으)로 설정되거나 지정되지 않았습니다(*Lax*(으)로 설정된 것으로 처리됨). `SameSite` = *Lax*&#x200B;이(가) 있으면 `POST` 요청을 통해 외부 URL로 쿠키를 전송할 수 없습니다.

## 솔루션

이 문제를 해결하려면 서드파티 서비스 공급자에게 문의하여 개발자에게 쿠키 매개변수를 구성하기 위해 통합을 업데이트하도록 요청하십시오.

## 관련 읽기

[Chrome SameSite 업데이트](https://www.chromestatus.com/feature/5088147346030592)
