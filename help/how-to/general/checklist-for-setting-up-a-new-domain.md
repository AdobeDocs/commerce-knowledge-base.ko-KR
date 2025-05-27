---
title: 새  [!DNL domain] 설정을 위한 체크리스트
description: Adobe Commerce 클라우드 인프라에서 새  [!DNL domain] 을(를) 설정하는 방법에 대한 검사 목록입니다.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 57535392a15294eebe97a161977fb697708bbe68
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 새 [!DNL domain] 설정을 위한 체크리스트

이 체크리스트에서는 클라우드 인프라의 Adobe Commerce에서 새 [!DNL domain]을(를) 설정하는 방법을 설명합니다. 새 도메인을 추가할지 또는 현재 도메인을 대체할지 여부에 관계없이 적용됩니다. 새 스테이징 환경을 가져온 후에도 적용됩니다(4단계 참조).

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 새 도메인을 설정하는 방법

### 1단계 - [!DNL Integration, Staging]에 대한 것입니까, 아니면 [!DNL Production environment]에 대한 것입니까?

* **[!DNL Integration]**: [!DNL Custom domains]은(는) 지원되지 않습니다. 대신 이 메서드를 사용해야 합니다. [여러 웹 사이트 또는 스토어 설정: 로컬 설치 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains).
* **[!DNL Staging]**: **단계 2**(으)로 이동합니다.
* **[!DNL Production]**: **단계 3**(으)로 이동합니다.

### 2단계 - [!DNL Staging environment]: [!DNL Pro] 또는 [!DNL Starter]에 계십니까?

* **[!DNL Pro]**: **요청을 제출**&#x200B;하여 [!DNL Fastly, Nginx]에 도메인을 추가하고 [!DNL SSL certificate]과(와) 필요한 경우 [!DNL Sendgrid domain]을(를) 구성합니다. 구성이 완료되면 [구성을  [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings)&#x200B;(으)로  [!DNL DNS] 업데이트합니다.

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

* **[!DNL Pro]**: **요청을 제출**&#x200B;하여 [!DNL Fastly, Nginx]에 도메인을 추가하고 [!DNL SSL certificate]을(를) 구성합니다(필요한 경우 [!DNL Sendgrid domain]&#x200B;(으)로). 구성이 완료되면 **4**&#x200B;단계를 계속합니다.

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

### 5단계 - [!DNL domain] 구성이 확인되었습니까?

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

즉, 이전에 `ece-tools` 패키지에서 `config:dump` 명령을 실행하여 빌드](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build)에서 [SCD를 설정했습니다.

만든 새 스토어/웹 사이트가 `app/etc/config.php` 파일에 표시되지 않는 경우 명령을 다시 실행하여 변경 내용이 데이터베이스에 있는 `config.php` 파일을 동기화한 다음 `config.php` 파일을 커밋하고 다시 배포해야 합니다. 새 저장소/웹 사이트에 대한 정적 콘텐츠를 적절한 파일 경로로 쉽게 배포할 수 있도록 하기 위한 것입니다.

## 관련 읽기

* [여러 웹 사이트 또는 스토어 설정: 사용 안내서의 새로 추가 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains).
* 원본 닫기로 인해 [사이트에 액세스할 수 없음](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/production-site-not-accessible-due-to-origin-cloaking)
