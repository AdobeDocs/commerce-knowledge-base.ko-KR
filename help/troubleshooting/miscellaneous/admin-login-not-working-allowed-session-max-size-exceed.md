---
title: '[!UICONTROL Admin] 로그인이 작동하지 않음 - 허용된 세션 최대 크기를 초과했습니다.'
description: '[!UICONTROL Admin] 패널에 로그인하려고 하면 양식이 새로 고쳐지고 로그인할 수 없는 문제를 해결합니다.'
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# [!UICONTROL Admin] 로그인이 작동하지 않음 - 허용된 세션 최대 크기를 초과했습니다.

이 문서에서는 [!UICONTROL Admin] 패널에 로그인하려고 하지만 양식이 새로 고침되어 로그인할 수 없거나 [!UICONTROL Admin] 패널에서 일부 작업을 수행하고 자동으로 로그아웃되는 경우에 대한 수정 사항을 제공합니다.
이는 [!UICONTROL Admin] [!UICONTROL Session Size]이(가) 초과되었기 때문입니다.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 문제

[!UICONTROL Admin]에서 다음 증상 중 하나가 발생합니다.

1. 양식이 다시 로드되기 때문에 [!UICONTROL Admin]에 로그인할 수 없습니다.
1. 작업을 수행하려고 하면 자동으로 로그아웃됩니다.

## 원인

허용된 세션 최대 크기를 초과했습니다.

## 솔루션

`var/log/support_report.log` 파일에서 다음과 같은 오류를 확인합니다.

*[2023-07-13T04:26:09.792060+00:00] 보고서.경고: 세션 크기260572 허용된 최대 세션 크기(256000)를 초과했습니다. [] []
[2023-07-13T04:26:17.056714+00:00] 보고서.경고: 세션 크기260570 허용된 세션 최대 크기를 초과했습니다. 2560005&rbrace;[]*[]

이러한 오류가 표시되면 해결 방법은 다음과 같습니다.

<u>Adobe Commerce 온-프레미스</u>:
1. 백 엔드 구성에서 **[!UICONTROL Max Session Size in Admin]** 값을 늘립니다. 이렇게 하려면 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**(으)로 이동합니다.
1. 값을 *500000* 이상으로 설정하십시오. 오류에 보고된 기존 최대 크기에 따라 값을 *0*(으)로 설정하여 세션 크기 제한을 제거할 수도 있습니다.

<u>클라우드 인프라의 Adobe Commerce</u>:

(이 설정은 배포/작업 모드가 *기본* 또는 *개발자*&#x200B;인 경우에만 [!UICONTROL Admin]에서 액세스할 수 있습니다. 그러나 클라우드 환경에서는 프로덕션 배포 모드만 허용됩니다.)

이 값을 늘리려면 터미널(SSH)에서 이 명령을 실행합니다.

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

오류에 보고된 기존 최대 크기에 따라 *500000*&#x200B;보다 높게 설정할 수 있으며 세션 크기 제한을 제거하려면 값을 *0*(으)로 설정할 수도 있습니다.

## 관련 읽기

* 관리 시스템 안내서의 [세션 크기](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions)
* 구성 가이드의 [작업 모드](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode)
* Commerce on Cloud Infrastructure Guide의 [보안 연결](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)
