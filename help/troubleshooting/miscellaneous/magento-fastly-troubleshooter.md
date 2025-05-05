---
title: Adobe Commerce Fastly 문제 해결사
description: Adobe Commerce 사용자를 위한 이 Fastly 문제 해결사는 표시되는 증상에 대한 응답을 기반으로 솔루션을 안내합니다. 질문을 클릭하여 다음 옵션 또는 답변을 확인합니다.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Adobe Commerce Fastly 문제 해결사

Adobe Commerce 사용자를 위한 이 Fastly 문제 해결사는 표시되는 증상에 대한 응답을 기반으로 솔루션을 안내합니다. 질문을 클릭하여 다음 옵션 또는 답변을 확인합니다.

## 1단계 - Fastly 서비스 확인 {#step-1}

+++**고객이 Fastly와 관련된 문제를 보고합니다. Fastly 서비스가 중단되었습니까?**

a. 예 - [Fastly 서비스 상태](https://status.fastly.com/)를 확인하고 [Adobe Commerce 지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.\
b. 아니요 - [2단계](#step-2)로 진행합니다.

+++

## 2단계 - VCL 구성 파일 확인 {#step-2}

+++**백 엔드 테스터를 실행할 때 오류가 발생했습니까?**

[백엔드 테스터 - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/)를 통해 프로젝트 URL을 실행합니다. 이 페이지에는 VCL 구성 파일의 버전(페이지를 캐시할 수 있는 경우), Fastly 모듈의 버전 및 기타 유용한 문제 해결 정보가 표시됩니다. 착오가 있으십니까?

a. 예 - _플러그 인 VCL 버전이 오래되었습니다! 다시 업로드하십시오._ 이 오류에 대한 해결 방법은 [Fastly 오류를 참조하십시오. 플러그 인 VCL 버전이 오래되었습니다! ](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md)을(를) 다시 업로드하십시오.\
b. 아니요 - [3단계](#step-3).

+++

## 3단계 - 이미지 최적화 오류 확인 {#step-3}

+++**이미지 최적화 오류**

a. 예 - [이미지 최적화를 사용하도록 설정하는 동안 오류가 발생했습니다](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. 아니요 - CLI/터미널에서 실행하여 DNS를 확인합니다. `dig [your website.com] + short`. [4단계](#step-4)로 진행합니다.

+++

## 4단계 - DNS 확인 {#step-4}

+++**`dig`을(를) 실행하면 어떻게 됩니까?**

`dig`을(를) 실행했을 때 prod.magentocloud.map.fastly.net 또는 다음 IP 주소 중 하나를 가리키는 레코드를 반환했습니다(개발자 설명서에서 [프로덕션 설정으로 DNS 구성 업데이트](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) 참조).

* 151.101.1.124
* 151.101.65.124
* 151.101.129.124
* 151.101.193.124

a. 예 - 이 문제는 DNS와 관련이 없습니다. [5단계](#step-5)로 진행합니다.\
b. 아니요 - 이 문제는 DNS와 관련이 있을 수 있습니다. 고객은 [DNS 구성을 확인](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings)하거나 DNS 공급자에게 자세한 내용을 문의해야 합니다.

+++

## 5단계 - 연결 확인 {#step-5}

+++**CLI/터미널에서 `curl -svo /dev/null "https://website.com"`을(를) 실행할 때 &quot;Connection Insecure&quot; 또는 &quot;Not Secure&quot; 메시지가 반환됩니까?**

a. 예 - 인증서 문제일 수 있습니다. 브라우저에서 웹 사이트를 방문하여 잠금 아이콘을 선택하고 인증서 만료를 찾습니다. [6단계](#step-6)로 진행합니다.\
b. 아니요 - [http://fastly-debug.com](https://www.fastly-debug.com/)을(를) 방문하여 [Adobe Commerce 지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)에서 이 정보를 공유하세요.

+++

## 6단계 - 유효한 TSL 인증서가 있는지 확인 {#step-6}

+++**인증서가 만료되었습니까?**

a. 예 - 인증 기관(CA)으로 TLS 인증서를 갱신해야 합니다.\
b. 아니요 - 인증서가 전혀 없을 수 있습니다. Adobe Commerce이 있는 경우 TLS 인증서를 구입하는 것이 좋습니다. 클라우드 인프라에서 Adobe Commerce을 사용하는 경우 Fastly에서 보안 HTTPS 트래픽을 제공하기 위해 도메인 유효성 검사 Let&#39;s Encrypt SSL/TLS 인증서를 가질 수 있습니다. 개발자 설명서에서 [SSL/TLS 인증서 프로비저닝](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)을 참조하십시오.

+++

[1단계로 돌아가기](#step-1)
