---
title: 'cURL 오류 60: SSL 인증서가 만료됨'
description: '이 문서에서는 cURL 오류 60: 클라우드 인프라의 Adobe Commerce에 있는 기본 또는 통합 분기에서 SSL 인증서가 만료된 후 분기를 마지막으로 배포한 시기를 확인하는 방법을 보여 줍니다.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# cURL 오류 60: SSL 인증서가 만료됨

이 문서에서는 클라우드 인프라의 Adobe Commerce에 있는 [!DNL Master] 또는 [!DNL Integration] 분기에서 `cURL error 60`을(를) 받은 후 분기가 마지막으로 배포된 시간을 확인하는 방법을 보여 줍니다. [!DNL SSL certificate]

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 원인

해당 분기의 [!DNL SSL certificates]은(는) 30일 동안만 유효하며 30일 이상 분기가 다시 배포되지 않았을 수 있습니다.

오류는 다음과 비슷합니다.

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>이 인증서는 [!DNL Let's Encrypt] 또는 [!DNL DigiCert]과(와) 같이 잘 알려진 외부 CA에서 서명되지 않았습니다. 테스트와 개발을 위해 Adobe 플랫폼에서 관리하며 인증서를 발급하는 루트를 명시적으로 신뢰하지 않는 한 브라우저나 curl에서 기본적으로 신뢰되지 않을 수 있습니다.

## 솔루션

분기가 마지막으로 배포된 시간을 확인합니다. 30일 임계값을 초과하는 경우 분기를 다시 배포합니다.

마지막 배포가 수행된 시기를 확인하는 두 가지 방법:

* [메서드 1: 사용 [!DNL magento-cloud] CLI](#meth2).
* [메서드 2:  [!DNL Project URL]](#meth3)을(를) 엽니다.

배포가 완료되면 [!DNL SSL certificate]이(가) 자동으로 갱신됩니다.

배포가 실패하여 이를 해결하는 데 도움이 필요한 경우 [지원 티켓을 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)하십시오.

### 방법 1: [!DNL magento-cloud] CLI 사용 {#meth2}

이 명령 실행: `magento-cloud activity:list --type=environment.push`

### 방법 2: [!DNL Project URL] 열기 {#meth3}

`https://demo.magento.cloud/#/projects/<project>/environments/<environment>`(으)로 이동하여 마지막 배포가 수행된 시기를 확인합니다.

## 관련 읽기

개발자 설명서에서:

* [Cloud Manager API: SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Fastly 설정: SSL/TLS 인증서 프로비저닝](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

지원 기술 자료에서:

* [사용자 지정 SSL 인증서 만료 정보](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce에 대한 [SSL(TLS) 인증서](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=ko)
