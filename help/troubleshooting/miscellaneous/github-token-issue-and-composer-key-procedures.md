---
title: Github 토큰 문제 및 작성기 주요 절차
description: 이 문서에서는 오래된 작성기 키로 인한 Github 토큰 실패와 관련된 배포 실패 문제에 대한 해결 방법을 제공합니다.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Github 토큰 문제 및 작성기 주요 절차

이 문서에서는 오래된 작성기 키로 인한 Github 토큰 실패와 관련된 배포 실패 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer 버전 1.10.20 이하

>[!NOTE]
>
>Adobe Commerce 온-프레미스 판매자는 Git에서 도입한 토큰 형식 변경 사항으로 인해 Composer 버전 1.10.21 이상을 사용하는지 호스트 공급자에게 확인해야 합니다.

## 문제

배포가 실패하고 배포 로그에 다음과 유사한 정보가 포함됩니다.

*치명적인 오류: 발견되지 않은 UnexpectedValueException: github.com에 대한 github oauth 토큰에 /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*&#x200B;에 잘못된 문자 &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot;가 포함되어 있습니다.

## 원인

오래된 작성기 키로 인해 Github 토큰이 실패하여 배포가 실패합니다.

## 솔루션

이 문제를 해결하려면 Composer 버전을 1.10.22로 업데이트하십시오.

1. 로컬 환경에서 `composer require “composer/composer”:”>1.10.21` 실행.
1. 이렇게 하면 해당 Composer 패키지 버전에 대한 요구 사항이 추가됩니다. 잠금 파일을 확인하십시오. `composer/composer` 버전은 1.0.22 이상이어야 합니다.
1. `composer.json` 및 `composer.lock`을(를) 커밋하고 배포를 푸시합니다.

이 메서드가 작동하지 않으면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

## 관련 읽기

* [Github 블로그: GitHub의 새로운 인증 토큰 형식 지원](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com 뉴스 문서: GitHub가 식별 가능성, 비밀 검색 및 엔트로피를 개선하기 위해 토큰 형식을 변경함](https://www.infoq.com/news/2021/04/github-new-token-format/)
