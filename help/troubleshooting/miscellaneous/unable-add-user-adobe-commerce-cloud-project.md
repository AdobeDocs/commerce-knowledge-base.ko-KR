---
title: Adobe Commerce 클라우드 프로젝트에 사용자를 추가할 수 없음
description: 이 문서에서는 Adobe Commerce 클라우드 프로젝트에 사용자를 추가할 수 없는 경우에 대한 솔루션을 제공합니다.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Adobe Commerce 클라우드 프로젝트에 사용자를 추가할 수 없음

이 문서에서는 클라우드 프로젝트에 사용자를 추가하려고 하지만 실패하고 오류가 발생하는 경우를 위한 솔루션을 제공합니다. *사용자 XXX가 없습니다*.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

이 문서에서는 Adobe Commerce 클라우드 프로젝트에 사용자를 추가할 수 없는 경우에 대한 솔루션을 제공합니다.

## 원인

이는 예상되는 비헤이비어입니다. 먼저 https://accounts.magento.cloud에서 사용자 계정을 만든 후 Adobe SSO에 연결하여 프로젝트에 사용자로 추가해야 합니다.

## 솔루션

1. 사용자에게 https://accounts.magento.cloud에서 계정에 로그인하도록 요청합니다 (해당 이메일 주소 아래 adobe.com에서 계정에 대해 이미 등록했어야 합니다.). https://account.adobe.com에 계정을 생성/보유하고 있다고 해서 자동으로 https://accounts.magento.cloud에 계정이 있는 것은 아닙니다.
참고: 사용자가 2022년 8월 이전에 account.magento.com 또는 accounts.magento.cloud에 계정이 있는 경우 2022년 8월 또는 그 이후에 계정을 만들지 않았다면 adobe.com에 계정이 없을 수도 있습니다. 사용자에게 Adobe 계정이 있고 로그인할 수 없는 경우 https://experienceleague.adobe.com/home#support에서 [지원 요청을 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)하고 세부 정보를 제공하십시오(문제 원인 = 사용자 관리).
1. 그런 다음 https://accounts.magento.cloud 로 이동해야 합니다.
1. 관리자가 작업을 완료하면 프로젝트에 사용자를 추가할 수 있습니다. 단계는 Commerce on Cloud Infrastructure 안내서의 [사용자 추가 및 액세스 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access)를 참조하십시오.

## 관련 읽기:

* Commerce on Cloud Infrastructure 안내서의 [사용자 액세스 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
* [Adobe Commerce 지원 또는 클라우드 계정에 로그인할 수 없음](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
