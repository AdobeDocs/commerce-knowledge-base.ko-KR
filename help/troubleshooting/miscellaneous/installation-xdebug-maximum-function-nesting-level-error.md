---
title: 설치 xdebug 최대 함수 중첩 수준 오류
description: 이 문서에서는 설치하는 동안 xdebug 최대 함수 중첩 수준 오류를 수정합니다.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# 설치 xdebug 최대 함수 중첩 수준 오류

이 문서에서는 설치하는 동안 xdebug 최대 함수 중첩 수준 오류를 수정합니다.

## 세부 사항

Adobe Commerce 설치 중에 다음과 유사한 메시지가 표시됩니다.

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

프로덕션 환경에서는 `xdebug`을(를) 사용하지 않는 것이 좋습니다.

## 솔루션

`xdebug`에 알려진 문제가 있어 Adobe Commerce 설치 또는 설치 후 상점 또는 Commerce 관리자 액세스에 영향을 줄 수 있습니다.

자세한 내용은 지원 기술 자료에서 [xdebug의 알려진 문제](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md)를 참조하십시오.
