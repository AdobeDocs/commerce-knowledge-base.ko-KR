---
title: GraphQL 요청을 위해 WAF을 우회하는 방법
description: 이 문서에서는 GraphQL 요청에 대해 WAF을 우회하는 방법을 설명합니다.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%
---
# GraphQL 요청을 위해 WAF을 우회하는 방법

이 문서에서는 [!DNL Fastly] WAF에서 GraphQL 요청을 차단하는 경우 WAF 요청을 우회하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce(모든 버전)

## 원인

GraphQL 요청의 고유한 특성으로 인해 [!DNL Fastly] WAF에 의한 요청의 거짓 양성 차단을 트리거할 수 있는 반복되는 문자가 많이 있을 수 있습니다.

## 솔루션

1. [!DNL Fastly] Magento 모듈을 통해 사용자 지정 코드 조각을 추가하여 이러한 요청에 대해 WAF을 건너뜁니다.

   유형: recv
   우선 순위: 15
   콘텐츠:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. **[!UICONTROL Upload VCL to Fastly]**&#x200B;을(를) 클릭합니다.

## 관련 읽기

* Commerce on Cloud Infrastructure 안내서의 [웹 응용 프로그램 방화벽(WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).
* Cloud Infrastructure의 Commerce 안내서에서 [사용자 지정 VCL 시작하기](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets).
