---
title: Adobe Commerce 2.4.0의 배송 라벨 작성 알려진 문제
description: 이 문서에서는 배송 레이블을 만들 수 없는 알려진 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Adobe Commerce 2.4.0의 배송 라벨 작성 알려진 문제

이 문서에서는 배송 레이블을 만들 수 없는 알려진 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>사전 요구 사항</u>: FedEx, DHL, UPS 또는 USPS 배송 방법을 사용하여 주문을 만듭니다.

### 시나리오 1: 선적을 추가할 때 레이블 생성

<u>재현 단계:</u>

1. **Sales** > **Orders** 아래의 관리자에서 주문한 주문을 엽니다.
1. **배송** 단추를 클릭합니다. **새 배송** 페이지가 열립니다.

<u>예상 결과:</u>

**배송 레이블 만들기** 확인란이 페이지 하단에 표시됩니다.

<u>실제 결과:</u>

**배송 레이블 만들기** 확인란이 표시되지 않습니다.

### 시나리오 2: 기존 선적에 대한 레이블 생성

<u>재현 단계:</u>

1. **Sales** > **Orders** 아래의 관리자에서 주문한 주문을 엽니다.
1. **배송** 단추를 클릭합니다. **새 배송** 페이지가 열립니다.
1. **배달 제출** 단추를 클릭합니다. 선적이 생성됩니다.
1. 새로 생성된 선적을 엽니다.
1. **배송 레이블 만들기** 단추를 클릭합니다. **패키지 만들기** 대화 상자가 열립니다.

<u>예상 결과:</u>

**패키지 만들기** 모달 창의 **패키지에 제품 추가** 단추에 주문 항목이 있는 필드가 표시됩니다.

<u>실제 결과:</u>

**패키지 만들기** 모달 창이 제대로 표시되지 않아서 배송 항목에 주문 항목을 추가할 수 없습니다.

## 솔루션

이 문서에 제공된 패치를 적용합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

패치는 왼쪽 열 탐색의 **패치** 아래에서 [Adobe Commerce 다운로드](https://magento.com/tech-resources/download) 페이지의 `.git` 및 `.composer` 형식에서도 다운로드할 수 있습니다. MC-35514 패치를 검색합니다.

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce on cloud infrastructure 버전 2.4.0
* Adobe Commerce 온-프레미스 버전 2.4.0

## 패치 적용 방법

지침은 [Adobe에서 제공한 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
