---
title: Headless Adobe Commerce 사이트에 Fastly가 필요합니까?
description: Headless Adobe Commerce 사이트에 Fastly가 필요합니까?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Headless Adobe Commerce 사이트에 Fastly가 필요합니까?

>[!NOTE]
>
>모든 고객은 프로덕션 및 스테이징 환경에 Fastly를 사용해야 합니다. Fastly는 클라우드 인프라 프로젝트에서 Adobe Commerce의 일부로 전체 페이지 캐싱, 이미지 최적화 및 보안 서비스(DDoS 및 WAF)를 제공하는 CDN(Content Delivery Network)입니다. 향상된 성능과 보안을 제공하는 Adobe Commerce 솔루션의 핵심 구성 요소입니다. 이러한 기능은 Adobe의 PCI 규정 준수의 일부입니다. 스타터 기본, 스테이징, Pro 스테이징 및 프로덕션 환경에서 이러한 Fastly 서비스를 설정해야 합니다. Headless 배포에서 Adobe Commerce을 사용하는 경우 공용 인터넷의 모든 API 트래픽이 Fastly를 통과해야 하며 GraphQL 응답을 캐시하기 위해 Fastly를 사용하는 것이 좋습니다. 개발자 설명서에서 [GraphQL 개발자 안내서 > Fastly를 사용한 캐싱](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly)을 참조하십시오.

## **질문**

Adobe Commerce의 Headless 구현을 개발 중입니다. Fastly를 CDN 서비스로 사용해야 합니까?

## **답변**

아니, 넌 몰라 이러한 상황에서는 Fastly 사용을 건너뛸 수 있습니다. 최소한 개발 초기에는 건너뛸 수 있습니다.

Headless 배포를 사용하지 않으려는 유일한 상황입니다.
개발자 설명서에서 [Adobe Commerce용 클라우드 > Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)를 참조하십시오.

그래도 SSL 인증서를 사용하려면 Fastly가 필요할 것입니다.

클라우드 인프라의 모든 Adobe Commerce 고객은 클라우드 구독 플랜의 일부로 Fastly에서 공유 SSL 인증서를 받습니다. Fastly에 자체 SSL 인증서를 추가하는 것은 별도의 다소 비싼 유료 옵션입니다. 따라서 Headless Adobe Commerce 웹 사이트에서도 라이브로 전환되기 전에 Fastly를 활성화하고 스테이징 및 프로덕션 환경에서 테스트하는 것이 좋습니다.

## 추가 정보

* [Headless 웹 사이트: 분리된 아키텍처의 주요 이점[Josh Koenig](https://pantheon.io/team/josh-koenig)의 ](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture).
* 개발자 설명서에서 [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)
