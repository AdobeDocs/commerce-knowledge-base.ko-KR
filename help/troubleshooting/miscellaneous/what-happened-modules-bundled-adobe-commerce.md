---
title: Adobe Commerce 2.4.4에서 모듈 누락
description: 이 문서에서는 이전 Adobe Commerce 버전에 포함된 모듈이 2.4.4에 없는 경우에 발생하는 문제에 대한 해결 방법을 제공합니다.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Adobe Commerce 2.4.4에서 모듈 누락

이 문서에서는 이전 Adobe Commerce 버전에 포함된 모듈이 2.4.4에 없는 경우에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드) 모든 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 문제

타사 모듈을 설치할 수 없거나 Adobe Commerce 2.4.4로 업그레이드할 때 핵심 번들 확장의 일부가 없는 것을 발견했습니다. 이는 Adobe Commerce 2.4.4에서 번들 확장 중 하나를 제거해야 하거나 프로젝트에서 제거된 모듈 중 하나의 기능을 일부 활용하는 경우에만 타사 모듈을 설치하는 결과여야 합니다.

* 시나리오 1: 프로젝트에서 핵심 번들 모듈의 기능 중 하나를 활용했습니다. 활용된 번들 모듈은 Adobe Commerce 2.4.4에 포함되어 있지 않습니다. Adobe Commerce 2.4.4로 성공적으로 업그레이드하면 모듈과 제공된 기능이 누락되었음을 알 수 있습니다.

* 시나리오 2: 현재 프로젝트에 제거된 번들 모듈 중 하나에 종속되는 모듈이 설치되어 있습니다.

공급업체 번들 확장이 Adobe Commerce 2.4.4 코드 베이스에서 제거되었으므로 이는 예상되는 동작입니다.

## 솔루션

공식 확장을 별도로 설치/구매합니다. [Commerce Marketplace](https://marketplace.magento.com/extensions.html)에서 사용할 수 있습니다.

## 관련 읽기

Adobe Commerce 설명서 > 릴리스 정보 > Adobe Commerce 2.4.4 릴리스 노트의 [공급업체 번들 확장](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions).
