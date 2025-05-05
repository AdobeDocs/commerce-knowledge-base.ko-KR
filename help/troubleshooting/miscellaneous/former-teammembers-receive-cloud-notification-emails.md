---
title: 이전 팀원이 Adobe Commerce 클라우드 알림 이메일을 받습니다.
description: 이 문서에서는 이전 팀원에게 전송되는 클라우드 인프라 알림 이메일에 대한 Adobe Commerce에 대한 솔루션을 제공합니다.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: bd199fac6d8f33491b9fa0f508b2bb52d56b46a5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# 이전 팀원이 Adobe Commerce 클라우드 알림 이메일을 받습니다.

이 문서에서는 다음과 같은 사용자를 수신자의 알림 이메일 목록에서 제거하는 솔루션을 제공합니다.

* 더 이상 프로젝트와 관련이 없는 이전 팀원
* 알림을 받지 않아야 하는 현재 팀원

## 문제

감지된 중단 또는 클라우드 프로젝트/환경과 관련된 중요한 문제에 대한 알림이 팀에 전송되었습니다. 여기에는 외부/에이전시 개발자 또는 시스템 통합자와 같이 더 이상 프로젝트와 연결되지 않을 수 있는 구성원이 포함됩니다. 이 사용자가 알림 수신을 중지하도록 합니다.

## 솔루션

>[!NOTE]
>
>외부/에이전시 개발자 또는 시스템 통합자로서 더 이상 프로젝트와 관련이 없는 경우 프로젝트 소유자 또는 해당 프로젝트의 프로젝트 관리자에게 지원을 요청해야 합니다.

프로젝트에서 사용자를 제거하여 알림을 중지하는 방법에는 두 가지가 있습니다.

* 방법 1: 클라우드 [!DNL Project URL]을(를) 사용합니다. 단계는 Commerce on cloud infrastructure guide의 [사용자 액세스 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=ko)를 참조하십시오.
* 방법 2: magento-cloud [!DNL CLI] 사용. 단계는 Commerce on cloud infrastructure guide의 [Manage users with the [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=ko#manage-users-with-the-cli)를 참조하십시오.

이미 이 작업을 수행했지만 이메일 알림에 해당 사용자가 계속 포함되는 경우 지원 티켓을 제출하여 계정의 *[!UICONTROL Always CC]* 설정에서 해당 사용자를 제거하도록 요청하십시오.

## 관련 읽기

* Commerce on cloud infrastructure 안내서에서 [사용자의 프로젝트 역할을 봅니다](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=ko#view-a-user&?lang=ko#39;s-project-role).
* [지원 알림에 팀원을 포함하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=ko)&#x200B;(Commerce KB).
