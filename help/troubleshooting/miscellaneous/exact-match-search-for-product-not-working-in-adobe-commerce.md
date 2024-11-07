---
title: Adobe Commerce 2.4.x에서 정확한 일치 검색이 작동하지 않음
description: 이 문서에서는 동일한 검색 문자열을 사용하는 스토어 전면 검색 결과가 Adobe Commerce 2.4.x와 Adobe Commerce 2.3.x의 차이가 있는 문제에 대한 설명을 제공합니다.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Adobe Commerce 2.4.x에서 정확한 일치 검색이 작동하지 않음

이 문서에서는 동일한 검색 문자열을 사용하는 스토어 전면 검색 결과가 Adobe Commerce 2.4.x와 Adobe Commerce 2.3.x의 차이가 있는 문제에 대한 설명을 제공합니다.

## 영향을 받는 제품 및 버전

- Adobe Commerce(모든 배포 방법) 2.4.x, 2.3.x
- 라이브 검색

## 문제

<u>필수 구성 요소:</u>

Adobe Commerce 2.3 및 Adobe Commerce 2.4 스토어 모두에 속성 값이 `Saga 1` 및 `Saga 16`인 제품이 있습니다.

<u>재현 단계:</u>

1. Adobe Commerce 2.3 기반 스토어의 앞에 있는 스토어에서 검색 필드에 *Saga 1*&#x200B;을(를) 입력하고 **검색**&#x200B;을 클릭합니다.
1. 검색 결과에서는 특성 값이 `Saga 1`인 제품만 가져옵니다.
1. Adobe Commerce 2.4 기반 스토어의 앞에 있는 스토어에서 검색 필드에 *Saga 1*&#x200B;을(를) 입력하고 **검색**&#x200B;을 클릭합니다.

<u>실제 결과:</u>

2.4에서 검색 결과에 특성 값이 `Saga 1` 및 `Saga 16`인 제품이 포함됩니다.

<u>예상 결과:</u>

2.4의 검색 결과는 2.3과 유사하며 특성 값이 `Saga 1`인 제품만 포함합니다.

## 원인

2.3.x에서 사용되는 Adobe Commerce 기본 검색 기능은 정확한 일치 검색 결과를 제공합니다. 라이브 검색 시 Adobe Commerce 2.4.x와 함께 릴리스된 설치할 수 있는 선택적 모듈인 라이브 검색은 다르게 구현되며 실제 결과는 모듈을 사용할 때 예상되는 비헤이비어입니다.

## 관련 읽기

사용 안내서에서 [Live Search 설치](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)

개발자 설명서에서 [실시간 검색](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview).
