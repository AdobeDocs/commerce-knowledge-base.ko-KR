---
title: 클라우드 인프라의 Adobe Commerce v2.3.5 GraphQL 캐싱 무효화가 작동하지 않음
description: 이 문서에서는 고객이 제품 정보를 변경할 경우 GraphQL 'GET' 요청이 오래된 정보를 반환하는 문제에 대한 패치를 제공합니다.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce v2.3.5 GraphQL 캐싱 무효화가 작동하지 않음

이 문서에서는 고객이 제품 정보를 변경할 경우 GraphQL `GET` 요청이 오래된 정보를 반환하는 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce v2.3.5.

## 문제

GraphQL 요청은 Fastly에 의해 캐시되며, 캐시된 버전은 Fastly의 후속 요청마다 검색됩니다. 제품이 Adobe Commerce 백엔드에 다시 저장되는 경우 제품이 업데이트되면 Fastly 캐시는 무효화되어야 합니다. 그러나 여전히 유효합니다.

<u>재현 단계</u>:

1. 다음과 같은 특정 카테고리에 대한 제품을 가져오려면 다음 GraphQL 요청을 트리거합니다.
   <pre><magento2-server>
    </pre>
1. Commerce 관리자에서 위의 요청으로 검색된 제품 중 하나를 다시 저장합니다.
1. 요청을 다시 트리거합니다.

<u>예상 결과</u>:

`X-Cache` 헤더에 `MISS`이(가) 포함되어 있습니다.

<u>실제 결과</u>:

`X-Cache` 헤더에 `HIT`이(가) 있습니다. 즉, 응답이 캐시됩니다.

## 솔루션

이 문서에 제공된 패치를 사용하여 GraphQL 제품 캐시를 비활성화합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce v2.3.5

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라의 Adobe Commerce v2.4.0
* Adobe Commerce 온-프레미스 v2.4.0
* 클라우드 인프라의 Adobe Commerce v2.3.5-p2
* Adobe Commerce 온-프레미스 v2.3.5-p2
* 클라우드 인프라의 Adobe Commerce v2.3.5-p1
* Adobe Commerce 온-프레미스 v2.3.5-p1
* Adobe Commerce 온-프레미스 v2.3.5
* 클라우드 인프라의 Adobe Commerce v2.3.4-p2
* Adobe Commerce 온-프레미스 v2.3.4-p2
* 클라우드 인프라의 Adobe Commerce v2.3.4
* Adobe Commerce 온-프레미스 v2.3.4
* Adobe Commerce 온-프레미스 v2.3.3-p1
* Adobe Commerce 온-프레미스 v2.3.3

## 패치 적용 방법

작성기 패치 적용 방법에 대한 지침은 [Adobe에서 제공하는 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
