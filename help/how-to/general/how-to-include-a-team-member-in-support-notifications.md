---
title: 지원 알림에 팀원을 포함하는 방법
description: 이 문서에서는 지원 알림에 팀원을 포함하는 방법에 대한 설명을 제공합니다.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 771793d45000e65c1bf41137cd984d2977b0a9ff
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# 지원 알림에 팀원을 포함하는 방법

이 문서에서는 팀 구성원이 이메일 알림을 통해 지원 업데이트를 자동으로 받도록 하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 원인

* 팀원이 필요한 권한을 가진 [!DNL cloud project]에 추가되지 않았습니다.
* 팀원에게 지원 계정이 없습니다.

## 솔루션

1. **[!DNL Cloud Project URL]**(예: `https://us-3.magento.cloud/projects/xxxxxx/edit`)로 이동합니다.
1. 팀 구성원이 프로젝트에 추가되었으며 [!DNL Super User]인지 확인하십시오.

프로젝트에 추가되지 않은 경우 [!DNL Super User] (으)로 추가하고 [!DNL Shared Access]을(를) 부여해야 합니다.

* 사용 안내서에서 [사용자 액세스 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
* [Adobe Commerce 기술 자료에서 사용자를 Commerce 클라우드 프로젝트에 추가할 수 없습니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html).
* [Adobe Commerce 도움말 센터 사용 안내서: Commerce 기술 자료에서 액세스 공유](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access).

[!DNL cloud project]에 추가되었지만 [!DNL Super User role]이(가) 없는 경우 [사용자 액세스 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)에서 해당 [!DNL role]을(를) 업데이트합니다.

## 관련 읽기

[이전 팀원이 Adobe Commerce 클라우드 알림 이메일을 받습니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
