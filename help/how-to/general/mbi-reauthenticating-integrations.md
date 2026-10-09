---
title: 'MBI: 통합 재인증'
description: 이 문서에서는 Magento Business Intelligence(MBI)에 서드파티 서비스에서 데이터를 가져오는 데 필요한 권한을 부여하는 통합을 다시 승인하는 솔루션을 제공합니다. 이러한 권한이 해지되면 재인증이 필요합니다.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3cd14413-6539-5c64-b063-fdcabf03abff
    internal-label: Commerce Intelligence
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# MBI: 통합 재인증

이 문서에서는 Magento Business Intelligence(MBI)에 서드파티 서비스에서 데이터를 가져오는 데 필요한 권한을 부여하는 통합을 다시 승인하는 솔루션을 제공합니다. 이러한 권한이 해지되면 재인증이 필요합니다.

## 데이터베이스 및 SaaS 통합

데이터베이스 및 SaaS 통합 목록은 개발자 설명서에서 [통합을 사용하여 외부 데이터 연결](https://experienceleague.adobe.com/ko/docs/commerce-business-intelligence/mbi/analyze/saas/integrations)을 참조하십시오. 페이지를 열 때는 탐색을 위해 왼쪽의 목차를 사용하십시오.

## 연결 문제가 있습니까?

통합을 인증하면 MBI에 서드파티 서비스에서 데이터를 가져오는 데 필요한 권한을 부여합니다. 이러한 권한이 해지되면 재인증이 필요합니다.

이 문제는 다음과 같은 여러 가지 이유로 발생할 수 있습니다.

* 서드파티 서비스의 문제
* 인증 토큰 만료
* 관리 계정에 대한 변경 사항
* 또는 MBI 내 내부 문제

모든 통합의 상태가 통합 페이지( **데이터 관리 > 통합**)에 있습니다.

![통합_page.png](assets/Integrations_page.png)

다시 인증하려면 계정 자격 증명을 다시 입력해야 할 수 있습니다. 경우에 따라 문제 통합을 위해 새 API 키를 생성해야 할 수 있습니다. 재인증 프로세스를 시작하려면 문제 통합의 이름을 클릭합니다.

문제가 지속되면 [지원 티켓을 제출](https://experienceleague.adobe.com/ko/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)하십시오.
