---
title: Adobe Commerce에서 이미지 최적화를 활성화하는 중 오류 발생
description: 이 문서에서는 이미지 최적화를 활성화하기 위해 Fastly에 연락하라는 알림과 함께 Fastly 이미지 최적화(IO)가 기본적으로 비활성화되어 있는 문제에 대한 해결 방법을 제공합니다. (Fastly Cloud Image Optimizer는 실시간 이미지 조작 및 최적화 서비스로 대역폭 효율적인 이미지를 제공하여 이미지 제공 속도를 높입니다.)
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Adobe Commerce에서 이미지 최적화를 활성화하는 중 오류 발생

이 문서에서는 이미지 최적화를 활성화하기 위해 Fastly에 연락하라는 알림과 함께 Fastly 이미지 최적화(IO)가 기본적으로 비활성화되어 있는 문제에 대한 해결 방법을 제공합니다. (Fastly Cloud Image Optimizer는 실시간 이미지 조작 및 최적화 서비스로 대역폭 효율적인 이미지를 제공하여 이미지 제공 속도를 높입니다.)

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x

## 문제

Fastly 구성 페이지의 Fastly IO 코드 조각 옆에 현재 상태가 표시됩니다. \_disabled \_아래에 다음 메시지가 있습니다. 영업 담당자에게 문의하거나 `support@fastly.com`(으)로 이메일을 보내 Fastly 서비스에 대한 이미지 최적화 활성화를 요청하십시오.

## 원인

사이트가 아직 활성화되지 않았을 수 있습니다. Fastly 데이터베이스에서 사이트가 실행될 때 사이트를 미리 로드하는 프로세스가 있습니다.

## 솔루션

[지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 만들고 이미지 최적화를 요청하세요.
