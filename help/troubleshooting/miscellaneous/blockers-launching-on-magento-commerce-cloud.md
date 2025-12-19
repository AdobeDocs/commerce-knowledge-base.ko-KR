---
title: 클라우드 인프라의 Adobe Commerce에서 시작되는 차단기
description: 이 문서에서는 Fastly 구성, SSL 인증서, 301 리디렉션 및 정적 에셋 성능과 관련된 문제를 포함하여 클라우드 인프라에서 Adobe Commerce을 시작할 수 있는 차단기에 대한 수정 사항을 제공합니다.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: 878abfdc4353122d808929f4834930a16b953e24
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에서 시작되는 차단기

이 문서에서는 Fastly 구성, SSL 인증서, 301 리디렉션 및 정적 에셋 성능과 관련된 문제를 포함하여 클라우드 인프라에서 Adobe Commerce을 시작할 수 있는 차단기에 대한 수정 사항을 제공합니다.

## &#x200B;1. Fastly 구성

[Fastly](https://www.fastly.com/)은(는) 정적 자산을 제공하는 바니시 기반 CDN(Content Delivery Network)입니다. 프로덕션 환경의 클라우드 인프라에서 Adobe Commerce에 필요하므로 Fastly를 구성하고 스테이징 및 프로덕션 환경 모두에서 Fastly를 활성화하고 구성한 웹 사이트(UAT)를 테스트하는 것이 중요합니다.

>[!WARNING]
>
>FPC(전체 페이지 캐시)가 활성화된 경우 웹 사이트가 다르게 수행됩니다. 시작하기 전에 테스트해야 합니다.

Fastly 구성 프로세스는 사용 안내서의 [Fastly 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 항목에 자세히 설명되어 있습니다. 다음은 중요한 단계입니다.

### 1a. 최신 버전의 Fastly 모듈이 설치되어 있는지 확인합니다.

최신 기능 및 개선 사항을 얻으려면 최신 버전의 Fastly 모듈이 설치되어 있는지 확인하십시오. 최신 버전의 Fastly가 있는지 확인하려면 사용 안내서에서 [Fastly 모듈 업그레이드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module)를 검토하세요. 자세한 내용은 사용 안내서에서 [Fastly 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)을 검토하세요.

### 1b. Commerce 관리자를 사용하여 Fastly 활성화 및 구성

자세한 내용은 사용 안내서에서 [Fastly 자격 증명 가져오기](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials)를 검토하세요.

### 1c. Fastly VCL 코드 조각 업로드

자세한 내용은 사용 안내서에서 [VCL을 Fastly에 업로드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)를 참조하십시오.

[사용자 지정 VCL 코드 조각을 만들고 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)할 수도 있습니다.

### 1d. Fastly를 위한 DNS 구성


자세한 단계는 이 문서를 참조하십시오. 사용 안내서의 [Fastly 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## &#x200B;2. 유효한 TLS(SSL) 인증서

문제: 유효하고 작동하는 SSL 인증서가 없으면 스테이징 환경의 체크아웃 페이지에서 외부 결제 방법을 테스트할 수 없습니다.

권장 사항 **:** 스테이징 또는 라이브 도메인 이름에 대한 공유 SSL 인증서를 요청합니다.


## &#x200B;3. 301 리디렉션 구성 및 테스트

문제: 301 리디렉션이 제공되지 않거나 제대로 구성되지 않아 스토어에서 SEO 등급 및 검색 목록이 감소했습니다.

권장 사항 **:** 301 리디렉션을 신중하게 구성하고 테스트하십시오.

이전 웹 사이트에서 새 웹 사이트로 마이그레이션하는 경우, 301 리디렉션은 이전에 색인화된 이전 페이지에서 새 스토어의 적절한 페이지로 고객을 유도합니다.

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**관련 문서:**

* 사용 안내서에서 [route.yaml을 통해 리디렉션](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html)합니다.
* 사용 안내서의 [클라우드 콘솔을 통해 리디렉션](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).
* 사용 안내서에서 [URL 재작성](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html).

## &#x200B;4. 자산 성과

문제: 정적 자산이 느리게 제공되므로 사이트의 성능이 저하됩니다(긴 로드 시간, 멀티미디어 콘텐츠가 표시되지 않음 등). 웹 사이트의 정적 자산은 CSS 리소스, 이미지, 비디오, 첨부 문서 등입니다. 이러한 구성 및 제공 방식은 사이트 성능의 핵심 요소입니다.

권장 사항: 성능 저하의 가능한 원인을 식별하려면 성능 테스트를 위해 [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit)을 사용하는 것이 좋습니다. 다음과 같은 타사 도구를 고려할 수도 있습니다.

* [Siege](https://www.joedog.org/siege-home): HTTP 로드 테스트 및 벤치마킹 유틸리티입니다. 기본 인증, 쿠키, HTTP, HTTPS 및 FTP 프로토콜을 지원합니다.
* [Jmeter](https://jmeter.apache.org/): 신뢰할 수 있는 부하 테스트 및 성능 측정 도구입니다. 급격한 트래픽(예: 플래시 판매)에 대한 성과를 측정하는 데 도움이 됩니다.
* [New Relic](https://support.newrelic.com/): 데이터, 쿼리, Redis 전송 등과 같이 작업당 추적 체류 시간으로 성능이 느린 사이트의 프로세스 및 영역을 찾습니다.
* [WebPageTest](https://www.webpagetest.org/)&#x200B;(무료) 및 [Pingdom](https://www.pingdom.com/)&#x200B;(유료): 원본 위치가 다른 사이트 페이지 로드 시간을 실시간으로 분석합니다.

CSS, JavaScript 및 HTML에 대해 [축소](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)를 고려할 수도 있습니다.

**관련 문서:**

* 개발자 설명서에서 [테스트 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html).
