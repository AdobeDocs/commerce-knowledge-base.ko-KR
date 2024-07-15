---
title: robots.txt 클라우드 인프라에 404 오류 Adobe Commerce 제공
description: 이 문서에서는 'robots.txt' 파일에서 클라우드 인프라의 Adobe Commerce에 404 오류가 발생하는 경우에 대한 수정 사항을 제공합니다.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt 클라우드 인프라에 404 오류 Adobe Commerce 제공

이 문서에서는 `robots.txt` 파일에서 클라우드 인프라의 Adobe Commerce에 404 오류가 발생하는 경우를 수정합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

`robots.txt` 파일이 작동하지 않으며 Nginx 예외가 발생합니다. `robots.txt` 파일은 동적으로 &quot;즉시&quot; 생성됩니다. Nginx에 모든 `/robots.txt` 요청을 존재하지 않는 `/media/robots.txt` 파일로 강제로 리디렉션하는 다시 작성 규칙이 있으므로 `/robots.txt` URL에서 `robots.txt` 파일에 액세스할 수 없습니다.

## 원인

일반적으로 Nginx가 제대로 구성되지 않은 경우 이 문제가 발생합니다.

## 솔루션

해결 방법은 `/robots.txt` 요청을 `/media/robots.txt` 파일로 리디렉션하는 Nginx 규칙을 사용하지 않도록 설정하는 것입니다. 셀프서비스가 활성화된 가맹점은 스스로 할 수 있고, 셀프서비스가 활성화되지 않은 가맹점은 지원 티켓을 만들 필요가 있다.

셀프서비스를 사용하도록 설정하지 않은 경우(또는 사용하도록 설정되었는지 확실하지 않은 경우) [Magento 지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 `/robots.txt` 요청에서 `/media/robots.txt`(으)로 Nginx 리디렉션 규칙 제거를 요청합니다.

셀프 서비스를 사용하도록 설정한 경우 ECE-Tools를 최소 2002.0.12로 업그레이드하고 `.magento.app.yaml` 파일에서 Nginx 리디렉션 규칙을 제거하십시오. 자세한 내용은 개발자 설명서에서 [사이트 맵 및 검색 엔진 로봇 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html)를 참조하십시오.

## 관련 읽기

* 지원 기술 자료에서 [Fastly 수준에서 Magento Commerce Cloud을 위한 악성 트래픽을 차단하는 방법](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md).
* 개발자 설명서에서 [사이트 맵 및 검색 엔진 로봇을 추가](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)합니다.
* 사용 안내서의 [검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).
