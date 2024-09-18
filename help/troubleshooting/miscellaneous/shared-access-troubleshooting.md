---
title: 공유 액세스 문제 해결
description: '**문제:** 신뢰할 수 있는 동료에게 공유 액세스 권한을 제공하려고 하지만 Commerce 계정 페이지에서 **공유 액세스** 탭을 찾을 수 없습니다.'
exl-id: 9e03c031-2359-42a6-9de4-943451a16456
feature: Cache
role: Developer
source-git-commit: ff863a9c8ebf3759c7ecf0549f79cc3a5efe4b46
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 공유 액세스 문제 해결

## 내 Commerce 계정 페이지(계정 소유자)에 [!UICONTROL Shared Access] 탭이 표시되지 않습니다.

**문제:** 신뢰할 수 있는 동료에게 공유 액세스 권한을 제공하려고 하지만 Commerce 계정 페이지에서 **[!UICONTROL Shared Access]** 탭을 찾을 수 없습니다.

**가능한 원인:** 공유 액세스 권한을 부여하는 데 필요한 권한이 Commerce 계정과 연결되어 있지 않습니다.

**해결 방법:** 계정 소유자(기본 계정 소유자)인 경우 Adobe 계정 팀에 문의하거나 [지원 티켓을 만드십시오](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). 이름과 계정과 연결된 이메일을 지정하십시오.

>[!NOTE]
>
>계정 소유자가 아닌 사용자도 계정에 **[!UICONTROL Shared Access]** 탭을 사용할 수 있습니다. 그러나 적절한 권한이 있는 계정 소유자(기본 계정 소유자)만 다른 사용자에게 공유 액세스를 제공할 수 있습니다. 공유 액세스에 대한 자세한 내용은 Adobe Commerce 도움말 센터 사용 안내서에서 [공유 액세스: 다른 사용자가 계정에 액세스할 수 있는 권한 부여](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#shared-access)를 참조하십시오.

## 공유 액세스를 사용했지만 특정 리소스에 대한 액세스 권한을 얻을 수 없습니다.

**문제:** 공유 액세스 계정으로 전환했지만 **[!UICONTROL Support tab]**&#x200B;에 액세스할 수 없습니다(예:).

**가능한 원인:** 지원 권한이 만료되었거나 지원에 대한 공유 액세스 권한이 부여되지 않았습니다.

**솔루션:**

1. **[!UICONTROL My Account]**(으)로 다시 전환합니다.
1. **[!UICONTROL Shared with me]** 탭을 클릭합니다.
1. 문제가 있는 **[!UICONTROL Shared Access]** 계정을 클릭하고 액세스 권한이 부여된 리소스를 검사합니다.
1. 특정 리소스가 누락된 경우 계정 소유자(기본 계정 소유자)에게 문의하십시오.

문제가 계속 발생하면 Adobe 계정 팀에 문의하십시오. 이름과 계정과 연결된 이메일을 지정하십시오.

## 공유 액세스를 사용하고 [!UICONTROL Support]을(를) 클릭했지만 새 티켓을 열 때 [!UICONTROL Organization] 드롭다운이 표시되지 않습니다.

**문제:** 공유 액세스 계정으로 전환했지만 **[!UICONTROL Support tab]**&#x200B;에 액세스할 수 없습니다(예:).

**가능한 원인:** 계정에 있는 한 상인에 대한 공유 액세스 권한만 부여되었습니다.

**솔루션:**

1. **[!UICONTROL My Account]**(으)로 다시 전환합니다.
1. **[!UICONTROL Shared Name]**&#x200B;이(가) 하나만 나열되면 티켓이 열릴 *기본 조직*&#x200B;이 됩니다.

문제가 계속 발생하면 Adobe 계정 팀에 문의하십시오. 이름과 계정과 연결된 이메일을 지정합니다.

## 공유 액세스를 사용했지만 공유 액세스 대신 내 티켓이 표시됩니다.

**문제:** 공유 액세스를 사용하여 도움말 센터에 액세스하지만 내 계정(조직)에 속한 티켓만 표시됩니다. Commerce 계정 페이지에 나를 위해 공유 액세스를 제공한 조직의 계정을 사용 중이지만 조직 티켓이 여전히 표시되지 않는 것이 표시됩니다.

**가능한 원인:** 브라우저에서 도움말 센터에서 캐시된 콘텐츠를 사용하고 있습니다.

**해결 방법:** 브라우저 캐시를 지우고 도움말 센터에 다시 액세스합니다(Commerce 계정 페이지에서 공유 액세스로 전환했는지 확인).

## 관련 읽기

[티켓 제출 양식: 판매자가 지원 기술 자료의 조직 드롭다운에 표시되지 않습니다](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).
