---
title: 새  [!DNL domain] 설정을 위한 체크리스트
description: Adobe Commerce 클라우드 인프라에서 새  [!DNL domain] 을(를) 설정하는 방법에 대한 검사 목록입니다.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 552a290b50f9e0c5fa740f26092c57bac447fe68
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# 새 [!DNL domain] 설정을 위한 체크리스트

이 체크리스트에서는 클라우드 인프라의 Adobe Commerce에서 새 [!DNL domain]을(를) 설정하는 방법을 설명합니다. 새 도메인을 추가할지 또는 현재 도메인을 대체할지 여부에 관계없이 적용됩니다. 새 스테이징 환경을 가져온 후에도 적용됩니다(4단계 참조).

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 새 도메인을 설정하는 방법

>[!NOTE]
>
>도메인 설정을 진행하기 전에 다음을 확인하십시오.
>
>모든 기본 URL은 올바른 웹 사이트 또는 스토어 보기의 범위에 있는 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**&#x200B;에서 HTTPS를 사용하도록 구성되어 있습니다.
>&#x200B;> [TLS](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/redirect-http-to-https-for-all-pages-on-cloud-force-tls#token_type=bearer&expires_in=10799996) 강제 적용을 사용하면 클라우드 인프라의 Adobe Commerce 사이트에서 모든 HTTP 트래픽을 HTTPS로 리디렉션할 수 있습니다.

### 1단계 - [!DNL Integration, Staging]에 대한 것입니까, 아니면 [!DNL Production environment]에 대한 것입니까?

* **[!DNL Integration]**: [!DNL Custom domains]은(는) 지원되지 않습니다. 대신 이 메서드를 사용해야 합니다. [여러 웹 사이트 또는 스토어 설정: 로컬 설치 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains).
* **[!DNL Staging]**: **단계 2**(으)로 이동합니다.
* **[!DNL Production]**: **단계 3**(으)로 이동합니다.

### 2단계 - [!DNL Staging environment]: [!DNL Pro] 또는 [!DNL Starter]에 계십니까?

* **[!DNL Pro]**: **요청을 제출**&#x200B;하여 [!DNL Fastly, Nginx]에 도메인을 추가하고 [!DNL SSL certificate]과(와) 필요한 경우 [!DNL Sendgrid domain]을(를) 구성합니다. 구성이 완료되면 [구성을  [!DNL DNS]  [!DNL development settings] (으)로 &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings)업데이트합니다.

>[!NOTE]
>
>PRO 아키텍처의 경우, 새 도메인을 추가하려면 Adobe Commerce에 지원 요청을 제출해야 합니다. 일부 고객은 Admin Console을 통해 Fastly를 수동으로 구성할 수 있지만 이는 도메인이 다른 Fastly 서비스 또는 프로젝트에 연결되지 않은 경우와 같은 제한된 경우에만 적용됩니다. 그러나 Nginx 구성은 항상 필요하며 이 단계는 Adobe에서 처리해야 합니다. 이러한 이유로 가장 신뢰할 수 있는 권장 방법은 [지원 티켓](https://experienceleague.adobe.com/home?support-tab=home#support)을 제출하고 Adobe에서 전체 도메인 설정 프로세스를 관리하도록 하는 것입니다.


* **[!DNL Starter]**: [!DNL Custom domains]은(는) 스테이징 환경에서 지원되지 않습니다.

### 3단계 - [!DNL Production environment]: [!DNL Pro] 또는 [!DNL Starter]에 계십니까?

* **[!DNL Pro]**: **요청을 제출**&#x200B;하여 [!DNL Fastly, Nginx]에 도메인을 추가하고 [!DNL SSL certificate]을(를) 구성합니다(필요한 경우 [!DNL Sendgrid domain]&#x200B;(으)로). 구성이 완료되면 **4**&#x200B;단계를 계속합니다.

>[!NOTE]
>
>사용 안내서의 [!DNL domain] > [!DNL Fastly] > [!DNL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** **[!UICONTROL Full Page Cache]**&#x200B;**[!DNL Fastly Configuration]**&#x200B;에서 **[!UICONTROL Domains]**&#x200B;의 구성을 업데이트하여 새 [[!DNL Manage domains]을(를) 직접 &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains)에 추가할 수 있습니다.
>
>
>도메인을 추가할 수 없는 경우 다음 이유 중 하나가 원인일 수 있습니다.
>
>1. 자체 [!DNL Fastly] 서비스에 구성된 온-프레미스에서 클라우드 환경으로 도메인을 마이그레이션하고 있습니다. 이 경우 요청을 제출하고 도메인의 위임을 요청합니다.
>1. 도메인을 Starter에서 Pro로 마이그레이션하고 있습니다. 이 경우 추가 지원 요청을 제출합니다.

* **[!DNL Starter]**: [!DNL domain] 탭에서 프로젝트에 **[!DNL Domains]**&#x200B;을(를) 추가한 다음 **요청을 제출**&#x200B;하여 **[!DNL ACME Challenge Key]**&#x200B;에 [!DNL SSL certificate]을(를) 제공합니다.

### 4단계 - [!DNL domain]이(가) 라이브입니까?

* **예**: [구성을  [!DNL DNS]  설정으로 업데이트[!UICONTROL production]합니다](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **아니요**: [&#x200B; [!DNL DNS]  설정으로 [!UICONTROL development]구성을 업데이트](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

### 5단계 - `magento-vars.php`에 도메인 리디렉션이 구성되어 있습니까?

도메인이 구성되면 [&#x200B; 파일에서 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables)변수를 수정`magento-vars.php`하여 도메인을 적절한 웹 사이트/스토어 URL로 이동해야 합니다.

### 6단계 - [!DNL domain] 구성이 확인되었습니까?

새 도메인에 대해 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**&#x200B;에서 새 저장소, 저장소 그룹 및 웹 사이트를 추가한 경우 `app/etc/config.php` 파일에 다음 섹션이 표시되는지 확인하십시오. 예:

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

즉, 이전에 [&#x200B; 패키지에서 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build) 명령을 실행하여 빌드`config:dump`에서 `ece-tools`SCD를 설정했습니다.

만든 새 스토어/웹 사이트가 `app/etc/config.php` 파일에 표시되지 않는 경우 명령을 다시 실행하여 변경 내용이 데이터베이스에 있는 `config.php` 파일을 동기화한 다음 `config.php` 파일을 커밋하고 다시 배포해야 합니다. 새 저장소/웹 사이트에 대한 정적 콘텐츠를 적절한 파일 경로로 쉽게 배포할 수 있도록 하기 위한 것입니다.

## 관련 읽기

* [여러 웹 사이트 또는 스토어 설정: 사용 안내서의 새로 추가 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains).
* 원본 닫기로 인해 [사이트에 액세스할 수 없음](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26856)
