---
title: 클라우드 인프라 UI에서 Adobe Commerce에 액세스할 수 없음
description: 이 문서에서는 클라우드 인프라 UI에서 Adobe Commerce에 로그인하지 못하고 "403 오류"가 발생하는 문제에 대한 해결 방법을 제공합니다.
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# 클라우드 인프라 UI에서 Adobe Commerce에 액세스할 수 없음

이 문서에서는 클라우드 인프라 UI에서 Adobe Commerce에 로그인하지 못하고 *403 오류*&#x200B;를 가져올 수 없는 문제에 대한 해결 방법을 제공합니다.

## 문제

클라우드 인프라 UI에서 Adobe Commerce에 처음 로그인하려고 하면 *403: 환경 액세스 거부됨* 오류가 발생합니다. 이 오류는 클라우드 URL로 처음 이동하면 마스터 분기가 로드되기 때문에 발생할 수 있으며, 해당 분기에 대한 액세스 권한이 없을 수 있습니다.

## 솔루션

URL에 처음 액세스할 때 403 오류가 발생하는 경우 마스터 분기에 역할이 있는지 확인하십시오.

1. 프로젝트의 라이선스 소유자 또는 슈퍼 사용자에게 с 연락하여 **환경 수준의 사용자**(개발자 설명서의 [클라우드 프로젝트 > Cloud Console에서 사용자 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console)에 설명됨)로서 사용자에게 액세스 권한을 제공했는지 확인하십시오.

   특정 분기에 적용 가능한 역할만 있는 경우 해당 분기의 URL로 이동해야 합니다. 예:
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   다음에 기본 URL에 액세스할 때 이 URL은 기본적으로 마지막으로 방문한 환경으로 설정됩니다.

1. 여전히 로그인할 수 없는 경우 с 개발자 설명서에서 [클라우드 프로젝트 > 프로젝트에 사용자 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project)에 설명된 대로 프로젝트의 라이선스 소유자 또는 슈퍼 사용자에게 연락하여 **프로젝트 수준 사용자**&#x200B;로 액세스 권한을 제공했는지 확인하십시오.
1. 오류가 계속되면 [지원 티켓을 제출](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)하십시오.
