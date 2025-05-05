---
title: 클라우드 인프라의 Adobe Commerce에 있는 모든 페이지에 대해 HTTP를 HTTPS로 리디렉션(TLS 적용)
description: Commerce 관리자에서 Fastly의 **TLS 강제 적용** 기능을 활성화하여 클라우드 인프라 스토어의 Adobe Commerce의 모든 페이지에 대해 글로벌 HTTP에서 HTTPS로 리디렉션할 수 있도록 합니다.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에 있는 모든 페이지에 대해 HTTP를 HTTPS로 리디렉션(TLS 적용)

Commerce 관리에서 Fastly의 **TLS 강제 적용** 기능을 활성화하여 클라우드 인프라 스토어에서 Adobe Commerce의 모든 페이지에 대해 전역 HTTP에서 HTTPS로 리디렉션할 수 있도록 설정합니다.

이 문서에서는 자세한 [단계](#steps), 강제 TLS 기능의 빠른 개요, 영향을 받는 버전 및 관련 문서에 대한 링크를 제공합니다.

## 단계 {#steps}

### 1단계: 보안 URL 구성 {#step-1-configure-secure-urls}

이 단계에서는 저장소의 보안 URL을 정의합니다. 이미 완료되면 [2단계: 강제 TLS 사용](#step-2-enable-force-tls)(으)로 이동합니다.

1. Commerce 관리자에 로그인합니다.
1. **스토어** > **구성** > **일반** > **웹**&#x200B;으로 이동합니다.
1. **기본 URL(보안)** 섹션을 확장합니다.    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. **보안 기본 URL** 필드에 스토어의 HTTPS URL을 지정하십시오.
1. **Storefront에서 보안 URL 사용** 및 **Admin에서 보안 URL 사용** 설정을 **예**(으)로 설정합니다.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. 변경 내용을 적용하려면 오른쪽 상단의 **구성 저장**&#x200B;을 클릭하세요.

**사용 안내서의 관련 설명서:**   [URL 저장](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-urls).

### 2단계: 강제 TLS 활성화 {#step-2-enable-force-tls}

1. Commerce 관리에서 **스토어** > **구성** > **고급** > **시스템**&#x200B;으로 이동합니다.
1. **전체 페이지 캐시** 섹션을 확장한 다음 **빠른 구성**&#x200B;을 확장한 다음 **고급 구성**&#x200B;을 확장합니다.
1. **TLS 강제 적용** 단추를 클릭합니다.    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. 표시되는 대화 상자에서 **업로드**&#x200B;를 클릭합니다.    ![magento-admin_force-tls-confirmation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. 대화 상자가 닫히면 Force TLS의 현재 상태가 **enabled**(으)로 표시되는지 확인하십시오.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**관련 Fastly 설명서:**   Adobe Commerce 2에 대해 [TLS 강제 적용 가이드](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md).

## 강제 TLS 정보

TLS(Transport Layer Security)는 보안 수준이 낮은 전임 SSL(Secure Socket Layer) 프로토콜을 대체하는 보안 HTTP 연결을 위한 프로토콜입니다.

Fastly의 TLS 강제 실행 기능을 사용하면 사이트 페이지에 대해 암호화되지 않은 모든 수신 요청을 TLS에 강제 적용할 수 있습니다.

&#x200B;>>
TLS에 해당하는 TLS로 리디렉션되는 암호화되지 않은 요청에 대해 *301 Moved Permanently* 응답을 반환하면 작동합니다. 예를 들어 *http://www.example.com/foo.jpeg*&#x200B;을(를) 요청하면 *https://www.example.com/foo.jpeg*(으)로 리디렉션됩니다.

[통신 보안](https://docs.fastly.com/guides/securing-communications/)(Fastly 설명서)

## 영향을 받는 버전

* 클라우드 인프라의 **Adobe Commerce:**
   * 버전: 2.1.4 이상
   * 계획: 클라우드 인프라의 Adobe Commerce 스타터 계획 아키텍처 및 클라우드 인프라의 Adobe Commerce 계획 아키텍처(Pro 레거시 포함)
* **빠르게:** 1.2.4

## routes.yaml에 변경 사항이 필요하지 않습니다.

저장소의 **모든** 페이지에서 HTTP에서 HTTPS로 리디렉션을 사용하려면 페이지를 `routes.yaml` 구성 파일에 추가할 필요가 없습니다. 이렇게 하면 전체 저장소에 대해 전역 TLS 강제 적용을 활성화하면 됩니다(Commerce 관리자 사용).

## 관련 Fastly 설명서

* [Adobe Commerce에 TLS 강제 적용 가이드](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [TLS 리디렉션 강제 적용](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [통신 보안](https://docs.fastly.com/guides/securing-communications/)
