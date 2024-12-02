---
title: 'PWA Studio: Adobe Commerce에 대한 Venia GraphQL 쿼리에서 유효성 검사 오류가 발생했습니다.'
description: 이 문서에서는 Adobe Commerce 인스턴스에 대한 Venia storefront GraphQL 쿼리가 유효성 검사 오류를 생성하는 문제를 해결하는 방법에 대한 권장 사항을 제공합니다.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: Adobe Commerce에 대한 Venia GraphQL 쿼리에서 유효성 검사 오류가 발생했습니다.

이 문서에서는 Adobe Commerce 인스턴스에 대한 Venia storefront GraphQL 쿼리가 유효성 검사 오류를 생성하는 문제를 해결하는 방법에 대한 권장 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce용 프로젝트 PWA Studio

## 문제

Adobe Commerce 온프레미스 또는 클라우드 인프라의 Adobe Commerce에 대한 Venia GraphQL 쿼리는 유효성 검사 오류를 생성합니다.

## 원인

문제를 일으키는 원인 중 하나는 Venia 및 해당 GraphQL 쿼리가 연결된 Adobe Commerce 인스턴스의 스키마와 동기화되지 않았기 때문일 수 있습니다.

## 솔루션

쿼리가 최신 상태인지 테스트하려면 프로젝트 루트에서 다음 명령을 실행합니다.

```bash
yarn run validate-queries
```

호환성 보고서를 표시합니다. 호환되지 않는 경우 PWA Studio 또는 Adobe Commerce 인스턴스를 업그레이드해야 합니다. 필요한 버전을 확인하려면 [Adobe Commerce 호환성 매트릭스](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/)를 확인하십시오.

업그레이드 방법에 대한 지침은 다음 설명서를 참조하십시오.

* PWA Studio 업그레이드를 위해 업그레이드해야 하는 버전에 대한 [PWA 릴리스 정보](https://github.com/magento/pwa-studio/releases/)의 &quot;이전 버전에서 업그레이드&quot; 섹션을 검색합니다.
* 개발자 설명서에서 [클라우드 인프라 버전에서 Adobe Commerce 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* 개발자 설명서에서 [Adobe Commerce 온-프레미스 업그레이드(&quot;작성기 만들기 프로젝트&quot; 또는 아카이브를 사용하여 설치됨)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade)
* 개발자 설명서에서 [Adobe Commerce 온-프레미스 업그레이드(Adobe Commerce 저장소를 복제하여 설치)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/developer/git-installs)

## 관련 읽기

* [PWA Studio: 지원 기술 자료에서 컴파일을 시작하기 전에 Webpack이 중지됨](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: 지원 기술 자료에서 개발자 모드를 실행할 때 유효성 검사 오류](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
* [PWA Studio: 브라우저가 지원 기술 자료에 &quot;프록시할 수 없음&quot; 오류](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)을(를) 표시합니다.
* 지원 기술 자료에서 [PWA Studio을 사용할 수 있도록 NPM을 구성](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md)
* [Adobe Commerce 설명서 PWA](https://magento.github.io/pwa-studio/)
