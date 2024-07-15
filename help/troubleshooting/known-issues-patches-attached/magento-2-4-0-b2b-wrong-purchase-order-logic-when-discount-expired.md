---
title: 'Adobe Commerce 2.4.0 B2B: 할인이 만료되었을 때 잘못된 구매 주문 논리'
description: 이 문서에서는 Adobe Commerce 2.4.0 B2B에서 PO(구매 주문) 할인이 적용되지 않는 알려진 문제에 대한 패치를 제공합니다. PO가 승인 프로세스 중에 만료된 할인 코드를 사용하여 PO를 수행한 경우 승인된 주문에 할인이 반영되지 않습니다.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B: 할인이 만료되었을 때 잘못된 구매 주문 논리

이 문서에서는 Adobe Commerce 2.4.0 B2B에서 PO(구매 주문) 할인이 적용되지 않는 알려진 문제에 대한 패치를 제공합니다. PO가 승인 프로세스 중에 만료된 할인 코드를 사용하여 PO를 수행한 경우 승인된 주문에 할인이 반영되지 않습니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0

## 문제

<u>필수 구성 요소</u>: 할인 쿠폰이 만들어졌고 PO가 자동으로 처리되지 않는 승인 규칙이 있습니다.

<u>재현 단계:</u>

1. 할인이 적용된 PO를 작성하십시오.
1. 할인 쿠폰을 비활성화합니다.
1. PO를 관리자로 승인합니다.
1. 결과로 생성된 주문을 확인합니다.

<u>예상 결과:</u>

주문이 할인된 금액으로 생성됩니다.

<u>실제 결과:</u>

전체 금액에 대해 주문이 생성됩니다.

## 솔루션

이 문서에 제공된 패치를 적용합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

패치는 왼쪽 열 탐색의 **패치** 아래에 있는 [Adobe Commerce 다운로드](https://magento.com/tech-resources/download) 페이지의 `.git` 및 `.composer` 형식에서도 다운로드할 수 있습니다. XXX 패치를 검색합니다.

## 패치 적용 방법

자세한 내용은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.
