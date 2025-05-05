---
title: 라이브 사이트에서 동일한 도메인을 사용하는 경우 프로덕션에서 Fastly 테스트
description: 프로덕션 도메인('example.com')에서 실행 중인 라이브 사이트가 있고 Fastly CDN이 활성화된 클라우드 인프라의 프로덕션 환경에서 Adobe Commerce에 있는 새 스토어를 테스트해야 하는 경우 실행 전 테스트 활동에 대해 이전에 Fastly에 추가한 하위 도메인('prod.example.com' 등)을 사용하는 것이 좋습니다. 이 문서에서는 자세한 내용을 살펴보고 관련 Adobe Commerce 설명서 리소스에 대한 유용한 링크를 제공합니다.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# 라이브 사이트에서 동일한 도메인을 사용하는 경우 프로덕션에서 Fastly 테스트

프로덕션 도메인(`example.com`)에서 실행 중인 라이브 사이트가 있고 Fastly CDN이 활성화된 클라우드 인프라의 프로덕션 환경에서 Adobe Commerce에 있는 새 스토어를 테스트해야 하는 경우 실행 전 테스트 활동에 대해 이전에 Fastly에 추가한 하위 도메인(`prod.example.com` 등)을 사용하는 것이 좋습니다. 이 문서에서는 자세한 내용을 살펴보고 관련 Adobe Commerce 설명서 리소스에 대한 유용한 링크를 제공합니다.

## 문제

`example.com` 프로덕션 도메인을 사용하는 현재 저장소가 활성 상태이며 운영 중입니다. 그러나 클라우드 인프라에서 Adobe Commerce으로 구축하고 프로덕션 환경에 배포된 Fastly 전체 페이지 캐시 서비스를 사용하는 새 스토어를 테스트해야 합니다.

문제는 Adobe Commerce on cloud infrastructure 프로젝트의 프로덕션 환경에서 동일한 라이브 도메인(`example.com`)을 사용하므로 새 사이트를 이 도메인으로 전환하여 동일한 도메인에서 현재 라이브 스토어를 동시에 실행할 수 없다는 것입니다.

### 프로덕션 환경에서 테스트하는 데 Fastly를 사용하는 이유는 무엇입니까?

이론적으로 Fastly CDN 사용을 건너뛰고 전체 페이지 캐시를 활성화하지 않고도 프로덕션 환경의 클라우드 인프라 저장소에서 Adobe Commerce을 테스트할 수 있습니다.

그러나 전체 페이지 캐시가 활성화된 경우 스토어의 성능은 다릅니다. 시작하기 전에 CDN으로 테스트하지 않았다면 사이트의 실제 라이브 성능을 알지 못할 것입니다. Fastly CDN이 활성화된 프로덕션에서 스토어를 테스트하는 것이 공식 Adobe Commerce 권장 사항입니다.

## 해결 방법: 프로덕션 하위 도메인 사용

기본 도메인(`example.com`)에 현재 라이브 사이트를 유지하면서 프로덕션 환경의 클라우드 인프라 저장소에 있는 새 Adobe Commerce에 첫 번째 수준 하위 도메인(`prod.example.com`)을 사용합니다.

클라우드 인프라 프로젝트에서 Adobe Commerce을 계획할 때 이러한 프로덕션 하위 도메인을 지정하고 클라우드 인프라 팀에 하위 도메인을 Fastly 서비스로 지정하도록 요청할 수 있습니다.

Adobe Commerce on cloud infrastructure 프로젝트 내에서 하위 도메인을 처리하려면 다음 단계를 따르십시오.

* [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Fastly 서비스/Nginx 구성에 하위 도메인을 추가할 것을 요청합니다(Cloud Infrastructure Pro 계획 아키텍처의 Adobe Commerce에 대해).
* 사용자 측에서 해당 DNS 설정을 구성합니다.

하위 도메인 구성에 대한 단계를 수행한 후 다음 단계를 수행하여 SSL 인증서에 대한 프로덕션 도메인의 유효성을 검사해야 합니다.

* 프로덕션 도메인의 SSL 유효성 검사를 위한 DNS TXT 레코드를 업로드합니다.
* SSL 인증서에 대한 프로덕션 도메인의 유효성을 검사하도록 요청하는 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

하위 도메인을 사용하면 해당 DNS 설정만 업데이트하면 되므로 나중에 스토어의 &quot;소프트 실행&quot;을 수행할 수 있습니다.

## 관련 설명서

지원 기술 자료에서:

* [스테이징 및 프로덕션 환경에서 Fastly DNS 설정 구성](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html?lang=ko)
* [클라우드에서 시작 플랜에 대한 Fastly 설정](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html?lang=ko)
* [클라우드 인프라의 Adobe Commerce에서 시작할 수 있는 차단기](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html?lang=ko)

개발자 설명서에서:

* [Fastly 개요](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=ko)
* [라이브 검사 목록: Fastly에 대한 DNS 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=ko)
