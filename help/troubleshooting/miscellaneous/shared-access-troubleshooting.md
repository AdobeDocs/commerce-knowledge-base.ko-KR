---
title: 공유 액세스 문제 해결
description: '**문제:** 신뢰할 수 있는 동료에게 공유 액세스를 제공하려고 하지만 Commerce 계정 페이지에서 **공유 액세스** 탭을 찾을 수 없습니다.'
exl-id: 9e03c031-2359-42a6-9de4-943451a16456
feature: Cache
role: Developer
source-git-commit: c2ccad480c89b974ffea7f2d4e2860e01882f833
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---

# 공유 액세스 문제 해결

## 내 Commerce 계정 페이지(계정 소유자)에 [!UICONTROL Shared Access] 탭이 표시되지 않습니다.

**문제:** 신뢰할 수 있는 동료에게 공유 액세스 권한을 제공하려고 하지만 Commerce 계정 페이지에서 **[!UICONTROL Shared Access]** 탭을 찾을 수 없습니다.

**가능한 원인:** 공유 액세스 권한을 부여하는 데 필요한 권한이 Commerce 계정과 연결되어 있지 않습니다.

**솔루션:**

* 계정 소유자(기본 계정 소유자)인 경우 Adobe 계정 팀에 문의하십시오. 팀원이 지원에 액세스할 수 있는 경우 [지원 티켓을 만드십시오](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#merchant-not-displayed). 계정과 연결된 이름 및 이메일을 지정합니다.
* 계정 소유자가 아닌 경우 공유 액세스 및 필요한 권한을 제공하기 위해 계정 소유자에게 문의해야 합니다.
* 계정 소유자가 더 이상 회사에 없는 경우 계정을 다른 사용자에게 전송하려면 [Commerce 계정 전송](https://experienceleague.adobe.com/ko/docs/commerce-admin/start/commerce-account/commerce-account-transfer)을 참조하세요.

>[!NOTE]
>
>계정 소유자가 아닌 사용자도 계정에 [!UICONTROL Shared Access] 탭을 사용할 수 있습니다. 그러나 필요한 권한이 있는 계정 소유자(기본 계정 소유자)만 다른 사용자에게 공유 액세스를 제공할 수 있습니다. 공유 액세스에 대한 자세한 내용은 Adobe Commerce용 Experience League 지원 사용 안내서에서 [공유 액세스: 다른 사용자가 계정에 액세스할 수 있는 권한 부여](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#shared-access)를 참조하십시오.

## 공유 액세스를 사용했지만 특정 리소스에 대한 액세스 권한을 얻을 수 없습니다.

**문제:** [!UICONTROL Shared Access] 계정으로 전환했지만 **[!UICONTROL Support tab]**&#x200B;에 액세스할 수 없습니다(예:).

**가능한 원인:** 지원 권한이 만료되었거나 지원에 대한 공유 액세스 권한이 부여되지 않았습니다.

**솔루션:**

1. **[!UICONTROL My Account]**(으)로 다시 전환합니다.
1. **[!UICONTROL Shared with me]** 탭을 클릭합니다.
1. 문제가 있는 **[!UICONTROL Shared Access]** 계정을 클릭하고 액세스 권한이 부여된 리소스를 검사합니다.
1. 특정 리소스가 누락된 경우 계정 소유자(기본 계정 소유자)에게 문의하십시오.

문제가 계속 발생하면 Adobe 계정 팀에 문의하십시오. 계정과 연결된 이름 및 이메일을 지정합니다.

## 공유 액세스를 사용하고 [!UICONTROL Support]을(를) 클릭했지만 조직에 대한 새 티켓을 열었을 때 양식에서 사용할 수 있는 제품이 없었습니다

**문제:** [Experience League](https://experienceleague.adobe.com/home?lang=ko#support)에서 티켓을 열 때 적절한 클라우드 프로젝트를 선택할 수 없습니다.

**가능한 원인:** [!DNL Commerce]개의 권한을 가진 올바른 조직을 선택하지 않았습니다.

**솔루션:**

1. ([!DNL Commerce]) 접미사를 사용하는 조직을 선택하십시오. [!DNL Commerce] 권한이 있는 조직입니다.

문제가 계속 발생하면 Adobe 계정 팀에 문의하십시오. 계정과 연결된 이름 및 이메일을 지정합니다.

## 공유 액세스를 사용하고 [!UICONTROL Support]을(를) 클릭했지만 [!DNL Commerce] 권한이 있는 조직의 새 티켓을 열 때 클라우드 프로젝트가 양식에 나열되지 않았습니다

**문제**: [Experience League](https://experienceleague.adobe.com/home?lang=ko#support)에서 티켓을 열 때 적절한 클라우드 프로젝트를 선택할 수 없습니다.

**가능한 원인**: 프로젝트에 추가되지 않았거나 프로젝트가 다른 라이선스와 연결되어 있을 수 있습니다(일부 조직에는 이름이 매우 유사한 자회사/관련 회사가 있을 수 있음).

**솔루션**:

1. 프로젝트에 추가되었는지 확인합니다. [사용자 액세스 관리](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/project/user-access)를 참조하십시오.
1. 계정 소유자로부터 프로젝트와 연결된 라이선스에 대한 공유 액세스 권한을 받았는지 확인합니다.

문제가 계속 발생하면 Adobe 계정 팀에 문의하십시오. 계정과 연결된 이름 및 이메일을 지정합니다.

## 공유 액세스를 사용하고 [!UICONTROL Support]을(를) 클릭했지만 새 티켓을 열 때 [!UICONTROL Organization] 드롭다운이 표시되지 않거나 해당 조직이 나열되지 않았습니다

**문제**: [!UICONTROL Shared Access] 계정으로 전환했지만 [Experience League](https://experienceleague.adobe.com/home?lang=ko#support)에서 티켓을 제출하려고 할 때 조직을 사용할 수 없거나 조직 이름이 드롭다운에 나열되지 않습니다.

**가능한 원인**: 계정에 있는 한 상인에 대한 공유 액세스 권한만 부여되었습니다.

**솔루션**:

1. **[!UICONTROL My Account]**(으)로 다시 전환합니다.
1. 공유 이름이 하나만 나열되면 티켓이 열리는 기본 조직이 됩니다.

문제가 계속 발생하면 Adobe 계정 팀에 문의하십시오. 계정과 연결된 이름 및 이메일을 지정합니다.

## 공유 액세스를 사용했지만 공유 액세스 대신 내 티켓이 표시됩니다.

**문제:** 공유 액세스를 사용하여 [도움말 센터](https://support.magento.com/hc/us-en/requests)에 액세스하고 있지만 내 계정(조직)에 속한 티켓만 표시됩니다. [!DNL Commerce] 계정 페이지에는 공유 액세스 권한을 제공한 조직의 계정을 사용 중이지만 조직 티켓이 여전히 표시되지 않습니다.

**가능한 원인:** 브라우저에서 도움말 센터에서 캐시된 콘텐츠를 사용하고 있습니다.

**해결 방법:** 브라우저 캐시를 지우고 도움말 센터에 다시 액세스합니다(Commerce 계정 페이지에서 공유 액세스로 전환했는지 확인).

## 관련 읽기

* [Adobe Commerce 지원 또는 클라우드 계정에 로그인할 수 없음](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project)
* [MageID 계정 소유자가 로그인하여 지원 티켓을 제출할 수 없습니다](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25231)
