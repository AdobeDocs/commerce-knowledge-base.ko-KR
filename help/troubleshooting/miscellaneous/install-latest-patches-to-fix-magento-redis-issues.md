---
title: Adobe Commerce Redis 문제 해결을 위한 최신 패치 설치
description: 이 문서에서는 [Adobe Commerce on cloud infrastructure Patches](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) 패키지에서 사용할 수 있는 최신 Redis 관련 패치에 대한 정보를 제공합니다.
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Adobe Commerce Redis 문제 해결을 위한 최신 패치 설치

이 문서에서는 [Adobe Commerce on cloud infrastructure Patches](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) 패키지에서 사용할 수 있는 최신 Redis 관련 패치에 대한 정보를 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce 2.3.3, 2.3.4

## 문제

Redis의 추가 CPU 및 메모리 소모는 Adobe Commerce 성능을 저하시킬 수 있으므로 웹 사이트의 전반적인 성능을 저하시킬 수 있습니다.

## 솔루션

Adobe Commerce on cloud infrastructure 패치 패키지에서 제공하는 최신 패치를 적용합니다. 자세한 지침은 개발자 설명서에서 [패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)을 참조하세요.

Adobe Commerce on cloud infrastructure Patches 패키지에서 제공하는 최신 Redis 패치는 다음과 같은 이점을 제공합니다.

* Redis를 위한 네트워킹 통신 규모 축소
* 추가 메모리 소비를 초래하는 경합 조건 해결
* 제거 사례를 처리하기 위해 캐시 어댑터 변경
* Redis CPU 사용량 감소

Adobe Commerce은 또한 클라우드 인프라 2.3.3 이상에서 Adobe Commerce을 실행하는 경우 Redis 5로 업그레이드할 것을 권장합니다.
