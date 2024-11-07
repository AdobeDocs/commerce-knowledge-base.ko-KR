---
title: 원본 클로킹으로 인해 사이트에 액세스할 수 없음
description: Adobe Commerce 이 문서에서는 클라우드 인프라 스테이징 또는 프로덕션 사이트 상점 및/또는 관리자에 액세스할 수 없는 경우에 대한 솔루션을 제공합니다.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# 원본 클로킹으로 인해 사이트에 액세스할 수 없음

Adobe Commerce 이 문서에서는 클라우드 인프라 스테이징 또는 프로덕션 사이트 상점 및/또는 관리자에 액세스할 수 없는 경우에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.3.x, 2.4.x

## 문제

https:/&#x200B;/mydomain.com.c.&lt;projectid>.magento.cloud/는 더 이상 액세스할 수 없습니다.

<u>재현 단계:</u>

1. 프로젝트에 로그인.
1. URL 및 SSH 목록을 보려면 **프로젝트 액세스**&#x200B;를 클릭합니다.

<u>실제 결과:</u>

다음 오류로 페이지가 로드되지 않음:

*NET::ERR\_CERT\_INVALID* *TLS 경고, 잘못된 인증서(554):*

<u>예상 결과:</u>

페이지가 정상적으로 로드되었습니다.

## 원인

원본 클로킹이 활성화되었으므로 더 이상 원본에 직접 액세스할 수 없습니다.

원본 클로킹은 Adobe Commerce이 DDoS 공격을 방지하기 위해 클라우드 인프라(원본)로 이동하는 모든 Non-Fastly 트래픽을 차단할 수 있는 보안 기능입니다.

## 솔루션

* 클라우드 사이트가 라이브 상태인 경우 https://mydomain.com/으로 전환합니다.
* https://mydomain.com/ 도메인을 사용하는 활성 사이트(클라우드 이외)가 있는 경우 하위 도메인 `mcprod.mydomain.com`을(를) 설정하고 대신 **기본 URL**&#x200B;을(를) *https://mcprod.mydomain.com*(으)로 업데이트한 다음 [DNS를 Fastly로 지정](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#update-dns-configuration-with-development-settings)합니다.

## 관련 읽기

지원 기술 자료의 [빠른 원본 차단 사용 FAQ](/help/faq/general/fastly-origin-cloaking-enablement-faq.md).
