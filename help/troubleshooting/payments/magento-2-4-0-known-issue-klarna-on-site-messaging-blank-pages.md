---
title: 'Adobe Commerce 2.4.0 알려진 문제: Klarna On-Site Messaging 빈 페이지'
description: 이 문서에서는 Klarna 결제 방법과 관련하여 알려진 Adobe Commerce 2.4.0 문제에 대해 설명합니다. 여기에서 디자인 테마를 지정하지 않고 Klarna 온사이트 메시지를 활성화하면 상점 첫 화면에 제품 페이지가 올바르게 표시되지 않습니다(제품 페이지가 비어 있음).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 알려진 문제: Klarna 온사이트 메시징 빈 페이지

이 문서에서는 Klarna 결제 방법과 관련하여 알려진 Adobe Commerce 2.4.0 문제에 대해 설명합니다. 여기에서 디자인 테마를 지정하지 않고 Klarna 온사이트 메시지를 활성화하면 상점 첫 화면에 제품 페이지가 올바르게 표시되지 않습니다(제품 페이지가 비어 있음).

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

<u>필수 구성 요소:</u> Klarna 결제 방법을 사용할 수 있습니다.

<u>재현 단계:</u>

1. Commerce 관리에서 **스토어** > **구성** > **판매** > **결제 방법** > **Klarna** > **Klarna 온사이트 메시징**(으)로 이동합니다.
1. **사용**&#x200B;을(를) *예*(으)로 설정합니다.
1. **디자인 테마** 필드를 비워 둡니다.
1. **구성 저장**&#x200B;을 클릭하여 구성을 저장합니다.
1. 상점 첫 화면으로 이동하여 제품 페이지를 탐색하십시오.

<u>예상 결과:</u>

Klarna 온사이트 메시지에 기본 디자인 테마를 적용한 상태로 페이지가 성공적으로 로드됩니다.

<u>실제 결과:</u>

빈 페이지가 표시됩니다.

## 솔루션

Klarna On-Site Messaging을 활성화하는 경우 항상 **디자인 테마** 필드가 비어 있지 않은지 확인하십시오.
