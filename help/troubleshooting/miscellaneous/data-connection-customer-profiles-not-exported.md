---
title: 고객 프로필이 Experience Platform에 표시되지 않음
description: 이 문서에서는  [!DNL Data Connection] 확장을 사용할 때 고객 프로필 데이터가 Experience Platform에 표시되지 않는 경우의 문제 해결 단계를 제공합니다.
feature: Personalization, Integration, Configuration
role: Admin, Developer
source-git-commit: a520ef45f1c55dbf34a98c4f4d3ab49814535434
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# 고객 프로필이 Experience Platform에 표시되지 않음

이 문서에서는 데이터 연결 확장을 사용할 때 고객 프로필 데이터가 Experience Platform에 표시되지 않는 경우 문제 해결 단계를 제공합니다.

## 영향을 받는 제품 및 버전

* [!DNL Data Connection] 확장이 설치된 Adobe Commerce 2.4.x

## 문제

[[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) 확장을 설치 및 구성하고 고객 프로필 데이터를 Experience Platform에게 보낼 수 있도록 했지만 해당 프로필 데이터가 Experience Platform에 표시되지 않습니다.

## 솔루션

고객 프로필 정보가 Experience Platform에 표시되지 않으면 다음을 확인하십시오.

### 최신 버전의 [!DNL Data Connection]이(가) 설치되었는지 확인

`experience-platform-connector` 확장의 최신 버전을 설치했는지 확인하십시오.

최신 버전에 대한 자세한 내용은 [[!DNL Data Connection] 확장 릴리스 노트](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes)를 참조하세요.

>[!NOTE]
>
>최신 버전의 [!DNL Data Connection] 확장에는 Experience Platform 데이터를 프로필로 보내는 `customers-connector` 모듈이 포함되어 있습니다. `customers-connector` 모듈은 버전 `1.2.0` 이상이어야 합니다.

### 고객 커넥터 모듈이 구성되었는지 확인합니다.

설치 시나리오에 따라 `customers-connector` 모듈이 구성되었는지 확인하십시오.

#### 클라우드 인프라의 Adobe Commerce

1. `.magento.env.yaml`에서 `ENABLE_EVENTING` 전역 변수를 사용하도록 설정합니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. 업데이트된 파일을 커밋하고 클라우드 환경으로 푸시합니다. 배포가 완료되면 다음 명령을 사용하여 이벤트 전송을 활성화합니다.

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Adobe Commerce 온-프레미스 설치

코드 생성 및 Adobe Commerce 이벤트를 활성화하려면 다음 명령을 실행합니다.

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Experience Platform 데이터를 캡처하여 프로필로 전송하도록 활성화했는지 확인

Commerce 관리에서 다음 필드가 설정되어 있는지 확인합니다.

* **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**&#x200B;에서 [!UICONTROL Back office events] 및 [!UICONTROL Customer profiles] 확인란이 활성화되어 있는지 확인합니다.
* *[!UICONTROL Profile Dataset ID]* 필드가 올바르고 동작 및 백 오피스 이벤트 데이터에 현재 사용하고 있는 것과 다른 데이터 세트인지 확인하십시오.

### 이벤트가 스테이징 또는 프로덕션으로 라우팅되는지 확인

1. 다음 명령을 실행하여 현재 Adobe Developer 환경을 표시합니다.

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. 환경이 *[!UICONTROL Stage]*(으)로 설정된 경우 다음 명령을 사용하여 환경을 *[!UICONTROL Production]*(으)로 변경하십시오.

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### 쿼리 이벤트 데이터 SaaS 테이블

다음 SQL 쿼리를 연결하고 실행하여 고객 프로필 레코드가
`event_data_saas` 테이블 및 오류가 없음을 확인합니다.

```sql
Copy code
select * from event_data_saas;
```

### 이벤트 게시 오류 처리

1. 다음 오류가 발생하면 샌드박스 및 프로덕션 SaaS 커넥터 키가 올바른지 확인하십시오.

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. 관리자의 *[!UICONTROL Commerce Services Connector]* 페이지로 이동하여 지정된 [!UICONTROL sandbox/production] 키가 올바르게 구성되었는지 확인하십시오. 또한 Commerce 계정 [!UICONTROL sandbox/production] 설정이 [!UICONTROL Commerce Services Connector]에 표시된 설정과 일치하는지 확인하십시오. [자세히](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey)를 알아보세요.

### 서비스 ID가 허용 목록에 추가하다에 있는지 확인하고 Adobe Commerce 지원을 통해 확인합니다.

1. Adobe Commerce에서 [!UICONTROL Commerce Services Connector] `serviceId`이(가) 허용 목록에 추가하다에 표시되는지 확인하십시오.
1. Adobe Commerce 상태를 확인하려면 [허용 목록에 추가하다 지원](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)에 문의하십시오.

## 관련 읽기

Commerce 서비스 사용 안내서에서 [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) 확장을 참조하십시오.
