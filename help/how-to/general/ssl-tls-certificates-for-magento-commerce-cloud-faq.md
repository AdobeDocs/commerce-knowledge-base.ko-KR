---
title: 클라우드 인프라의 Adobe Commerce에 대한 SSL(TLS) 인증서
description: 이 문서에서는 클라우드 인프라의 Adobe Commerce 사이트에 대한 SSL(TLS) 인증서를 가져오는 방법에 대한 빠른 답변을 제공합니다.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 7694e6cb739d73a28c902e95d324b1317f4daaf6
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에 대한 SSL(TLS) 인증서

이 문서에서는 클라우드 인프라의 Adobe Commerce 사이트에 대한 SSL(TLS) 인증서를 가져오는 방법에 대한 빠른 답변을 제공합니다.

## Adobe에서 제공하는 SSL/TLS 인증서는 무엇입니까?

Adobe은 [!DNL Fastly]에서 보안 HTTPS 트래픽을 제공하기 위해 도메인 유효성 검사 [SSL/TLS 인증서를 암호화하겠습니다](https://letsencrypt.org/). Adobe은 클라우드 인프라의 각 Adobe Commerce Pro 계획 아키텍처, 스테이징 및 Adobe Commerce 클라우드 인프라의 시작 계획 아키텍처 환경에서 해당 환경의 모든 도메인을 보호할 수 있는 하나의 인증서를 제공합니다.

## 인증서는 무엇을 포함합니까?

Pro 플랜 아키텍처의 경우, 스테이징 및 프로덕션 전용 환경 모두에 SSL 인증서가 생성됩니다. PaaS(Platform-as-a-Service) 통합 환경 외부의 각 전용 환경에서는 해당 환경에 할당된 URL에 대해 이 인증서를 갖게 됩니다.

스타터 플랜 아키텍처 및 PaaS 통합 환경의 경우 환경과 함께 프로비저닝되고 별도의 인증서로 보호되는 기본 기술 도메인이 있습니다.

## 기존 인증서에 대한 새 도메인을 추가하는 방법

[!DNL Fastly]의 서비스에 도메인을 추가하려면 다음을 수행하십시오.

1. DNS의 도메인을 prod.magentocloud.map.fastly.net으로 지정하고 최대 6시간 동안 기다립니다.
1. [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Nginx 구성에서 이 도메인을 추가할 것을 요청합니다(이전에 수행하지 않은 경우).

## 인증서를 요청하는 방법

사례 1

아직 웹 사이트를 시작하지 않은 경우 고객 기술 관리자(CTA)로부터 ACME Challenge CNAME을 받았을 수 있습니다. DNS를 프로덕션 URL로 바로 지정할 수 없고 미리 생성된 SSL 인증서를 가져와야 하는 경우에만 ACME 문제가 필요합니다.

사례 2

사이트가 이미 라이브되어 있거나 라이브 사이트에 사용될 URL을 바로 지정할 수 있는 경우 ACME CNAME을 요청할 필요가 없습니다. 필요에 따라 클라우드 인프라 사이트의 Adobe Commerce에 URL을 추가하고 [!DNL Fastly]에 DNS를 가리키면 HTTP 유효성 검사가 작동하여 SSL 인증서를 처음 만들거나 추가 URL로 인증서를 업데이트합니다.

## 나만의 SSL/TLS 인증서를 사용할 수 있습니까?

Adobe에서 제공한 [인증서를 암호화하겠습니다](https://letsencrypt.org/). 대신 SSL/TLS 인증서를 제공할 수 있습니다.

그러나 이 프로세스를 설정하고 유지 관리하려면 추가 작업이 필요합니다. 먼저 웹 사이트의 도메인 이름(또는 일반 이름)에 대한 CSR(인증서 서명 요청)을 생성하고 SSL 인증서를 제공하도록 SSL 공급업체에 제공해야 합니다.

SSL 인증서가 있으면 [Adobe Commerce 지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 제출하거나 CTA과 함께 클라우드 환경에 사용자 지정 호스팅 인증서를 추가합니다.

* 더 이상 사용되지 않는 도메인은 시스템에서 자동으로 제거되며, 추가 작업이 필요하지 않습니다.
* 이미 인증서를 소유하고 있는 경우 SFTP(SSH File Transfer Protocol) 클라이언트를 사용하여 서버의 웹에 액세스할 수 없는 파일 위치에 인증서를 업로드하고 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 파일 경로를 알 수 있습니다.

>[!WARNING]
>
>인증서 파일을 티켓에 직접 업로드하지 않는 것이 중요합니다. 그렇지 않으면 인증서가 손상된 것으로 간주되므로 Adobe에서 새 인증서를 요청해야 합니다.
>파일을 SFTP를 통해 원하는 폴더로 서버에 업로드해야 합니다(예: `var/ssl`, `/tmp/ssl` 등). - 파일을 저장소에 커밋하는 것과 같은 다른 방법은 사용하지 마십시오(중요한 데이터가 포함되지 않은 변경 불가능한 파일에 대해서만 수행되어야 함).

## 인증서 이름

SSL 인증서의 이름은 기본 URL에만 해당되며, 첫 번째 URL에 의해 이름이 지정된 기본 호스트 이름이므로 일치해야 확인 및 생성될 수 있습니다. URL이 몇 개 있는 경우 인증서에 주체 대체 이름 항목으로 추가됩니다. 클라우드 인프라 사이트에서 하나의 Adobe Commerce을 가리키는 여러 URL이 있는 경우 하나의 공통 이름 URL 인증만 있으며, 이 인증에는 SSL로 사이트를 보호하기 위해 제목 대체 이름이 추가됩니다.

## 인증서의 일반 이름 필드에 표시될 도메인은 무엇입니까?

인증서에 표시된 도메인은 TLS 인증서에 추가된 첫 번째 도메인일 뿐이며, **일반 이름**(**CN**) 필드를 채우고 브라우저에서는 이 이름을 먼저 표시합니다. **주체 대체 이름**(**SAN**) 필드에 TLS 인증서에 대한 모든 DNS 이름이 포함되어 있습니다. 표시된 일반 이름을 변경하거나 요청할 방법이 없습니다.

## 와일드카드 TLS 인증서를 사용할 수 있습니까?

와일드카드 TLS 인증서는 사용자 정의 인증서에만 사용할 수 있고 Adobe Commerce Let&#39;s Encrypt 인증서에는 사용할 수 없습니다. TLS 최적화의 일환으로 Adobe은 와일드카드 TLS 인증서에 대한 지원을 종료합니다. Adobe의 Let&#39;s Encrypt 인증서를 사용하여 와일드카드 인증서를 사용하며 Adobe Commerce용 [!DNL Fastly] 콘솔에 구성된 판매자를 식별하고 연락하고 있습니다. 우리는 TLS의 적용 범위를 보장하기 위해 이러한 와일드카드 인증서를 정확한 도메인으로 바꿀 것을 요구하고 있다. 와일드카드 TLS 인증서를 바꾸려면 [!DNL Fastly] 플러그인의 [도메인 섹션](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains)을(를) 방문하십시오. 여기서 정확한 도메인을 추가하고 와일드카드를 제거할 수 있습니다. CDN을 통해 라우팅하려면 DNS가 이러한 새 도메인에 대해 [!DNL Fastly]을(를) 가리켜야 합니다. 도메인이 추가되고 DNS가 업데이트되면 일치하는 [Let&#39;s Encrypt](https://letsencrypt.org/) 인증서가 제공됩니다. 와일드카드를 사용하여 [!DNL Fastly]을(를) 가리키는 도메인을 제거하지 않으면 Adobe에서 공유 인증서를 삭제합니다. URL FQDN을 구성하지 않고 DNS에 동일한 URL FQDN을 설정하면 사이트가 중단될 수 있습니다. 따라서 구성된 URL도 [!DNL Fastly]을(를) 가리키는 DNS에서 일대일 일치하는지 확인해야 합니다.

## 도메인이 더 이상 Adobe Commerce을 가리키지 않으면 어떻게 해야 합니까?

도메인이 더 이상 Adobe Commerce을 가리키지 않는 경우 [!DNL Fastly]/Adobe Commerce 시스템에서 제거하십시오. 자세한 내용은 [!DNL Fastly] [도메인 삭제](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain)를 참조하십시오. 도메인을 Adobe Commerce으로 가리킬 필요는 없지만 최상위 도메인 TLS 인증서가 필요한지 확인하십시오. 최상위 도메인이 필요한 경우 Adobe Commerce을 가리키도록 DNS를 업데이트하십시오. 이미 Adobe Commerce을 가리키고 있는 경우 [lets-encrypt](https://letsencrypt.org/)를 포함하도록 CAA 레코드를 업데이트하십시오. 이 단계를 수행하면 LE 인증서가 포함된 필요한 보조 URL로 업데이트된 것이 표시됩니다&#x200B;.

## 관련 읽기

개발자 설명서에서 [SSL/TLS 인증서 프로비저닝](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)
