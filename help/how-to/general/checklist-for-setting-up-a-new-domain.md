---
title: 새  [!DNL domain] 설정을 위한 체크리스트
description: Adobe Commerce 클라우드 인프라에서 새  [!DNL domain] 을(를) 설정하는 방법에 대한 검사 목록입니다.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# 새 [!DNL domain] 설정을 위한 체크리스트

클라우드 인프라의 Adobe Commerce에서 새 [!DNL domain]을(를) 설정하는 방법에 대한 체크리스트입니다. 새 도메인을 추가하는지 아니면 현재 도메인을 새 도메인으로 바꾸는지에 관계없이 적용됩니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 새 도메인을 설정하는 방법

### 1단계 - [!DNL Integration, Staging]에 대한 것입니까, 아니면 [!DNL Production environment]에 대한 것입니까?

* **[!DNL Integration]**: [!DNL Custom domains]은(는) 지원되지 않습니다. 대신 이 메서드를 사용해야 합니다. [여러 웹 사이트 또는 스토어 설정: 로컬 설치 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains).
* **[!DNL Staging]**: **단계 2**(으)로 이동합니다.
* **[!DNL Production]**: **단계 3**(으)로 이동합니다.

### 2단계 - [!DNL Staging environment]: [!DNL Pro] 또는 [!DNL Starter]에 계십니까?

* **[!DNL Pro]**: **요청을 제출**&#x200B;하여 [!DNL Fastly, Nginx]에 도메인을 추가하고 [!DNL SSL certificate]과(와) 필요한 경우 [!DNL Sendgrid domain]을(를) 구성합니다. 구성이 완료되면 [구성을  [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings)(으)로  [!DNL DNS] 업데이트합니다.

>[!NOTE]
>
>사용 안내서의 [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains)과(와) 같이 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]**&#x200B;의 [!DNL Admin]에서 구성을 업데이트하여 새 [!DNL domain]을(를) 직접 [!DNL Fastly]에 추가할 수 있습니다.
>
>도메인을 추가할 수 없는 경우 다음 이유 중 하나가 원인일 수 있습니다.
>
>1. 고유한 [!DNL Fastly] 서비스에 구성된 클라우드 환경으로 도메인을 마이그레이션하고 있습니다. 이 경우 요청을 제출하고 도메인의 위임을 요청합니다.
>1. 도메인을 Starter에서 Pro로 마이그레이션하고 있습니다. 이 경우 추가 지원 요청을 제출합니다.

* **[!DNL Starter]**: [!DNL Custom domains]은(는) 스테이징 환경에서 지원되지 않습니다.

### 3단계 - [!DNL Production environment]: [!DNL Pro] 또는 [!DNL Starter]에 계십니까?

* **[!DNL Pro]**: **요청을 제출**&#x200B;하여 [!DNL Fastly, Nginx]에 도메인을 추가하고 [!DNL SSL certificate]을(를) 구성합니다(필요한 경우 [!DNL Sendgrid domain](으)로). 구성이 완료되면 **4**&#x200B;단계를 계속합니다.

>[!NOTE]
>
>사용 안내서의 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains)에서 [!DNL Admin]의 구성을 업데이트하여 새 [!DNL domain]을(를) 직접 [!DNL Fastly]에 추가할 수 있습니다.
>
>
>도메인을 추가할 수 없는 경우 다음 이유 중 하나가 원인일 수 있습니다.
>
>1. 자체 [!DNL Fastly] 서비스에 구성된 온-프레미스에서 클라우드 환경으로 도메인을 마이그레이션하고 있습니다. 이 경우 요청을 제출하고 도메인의 위임을 요청합니다.
>1. 도메인을 Starter에서 Pro로 마이그레이션하고 있습니다. 이 경우 추가 지원 요청을 제출합니다.

* **[!DNL Starter]**: **[!DNL Domains]** 탭에서 프로젝트에 [!DNL domain]을(를) 추가한 다음 **요청을 제출**&#x200B;하여 [!DNL SSL certificate]에 **[!DNL ACME Challenge Key]**&#x200B;을(를) 제공합니다.

### 4단계 - [!DNL domain]이(가) 라이브입니까?

* **예**: [구성을 [!UICONTROL production] 설정으로 업데이트 [!DNL DNS] 합니다](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **아니요**: [[!UICONTROL development] 설정으로  [!DNL DNS] 구성을 업데이트](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## 관련 읽기

* [여러 웹 사이트 또는 스토어 설정: 사용 안내서의 새로 추가 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains).
