---
title: 'Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 알려진 문제: dotdigital 로그인'
description: 이 문서에서는 dotdigital 계정이 활성화되어 있을 때 관리 패널을 통해 [dotdigital](https://dotdigital.com/)에 로그인할 수 없는 Adobe Commerce 2.3.6, 2.4.0-p1 및 2.4.1의 알려진 문제에 대해 설명합니다.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 38b4d310cab9dccad142c244f6e07f8421a9894d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 알려진 문제: dotdigital 로그인

이 문서에서는 Dotdigital 계정이 활성화되어 있을 때 [관리] 패널을 통해 [dotdigital](https://dotdigital.com/)에 로그인할 수 없는 Adobe Commerce 2.3.6, 2.4.0-p1 및 2.4.1 알려진 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.6(Safari 브라우저만 해당)
* Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.4.0-p1(Safari 브라우저만 해당)
* Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.4.1(Safari 브라우저만 해당)

## 문제

<u>필수 구성 요소</u>:

1. dotdigital 계정이 있습니다.
1. Adobe Commerce에 유효한 Dotdigital API 자격 증명이 있습니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **DOTDIGITAL** > **채팅 설정** > **활성화됨**&#x200B;이(가) *예*(으)로 설정되어 있습니다.
1. **채팅 위젯 구성** 또는 **채팅 팀 구성**&#x200B;에서 **구성**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

채팅 설정 페이지가 관리 패널을 통해 성공적으로 열립니다.

<u>실제 결과</u>:

Dotdigital에 로그인할 수 없습니다.

## 솔루션

해결 방법: 이 특정 상황에 대해 Safari를 대체할 수 있는 브라우저를 사용하십시오.