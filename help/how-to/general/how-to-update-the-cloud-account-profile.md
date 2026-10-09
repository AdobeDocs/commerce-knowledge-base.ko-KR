---
title: 클라우드 계정 프로필을 업데이트하는 방법
description: 이 문서에서는 Cloud 계정에서 프로필을 수정하는 단계를 제공합니다.
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%
---
# 클라우드 계정 프로필을 업데이트하는 방법

이 문서에서는 Cloud 계정에서 프로필을 수정하는 방법에 대한 단계를 제공합니다.

## 솔루션

클라우드 계정에서 프로필을 수정할 때 다음 필드를 수정할 수 있습니다.

1. [!UICONTROL First name]
1. [!UICONTROL Last name]
1. [!UICONTROL Username]

   >[!NOTE]
   >
   >Cloud Console 사용자 이름을 업데이트하면 프로젝트 URL이 `https://console.adobecommerce.com <old-username>/<project-id>`에서 `https://console.adobecommerce.com/<new-username>/<project-id>`(으)로 변경됩니다.
   >
   >업데이트 후에는 이전 URL을 사용하는 링크가 더 이상 작동하지 않습니다. 팀원은 새 URL을 사용하려면 저장된 책갈피, 내부 설명서 및 자동화를 업데이트해야 합니다.
   >
   >이 변경 사항은 새 Cloud Console URL에만 적용됩니다. 레거시 프로젝트 URL(`https://<region>.magento.cloud/projects/<project-id>`)은 사용자 이름을 사용하지 않으며 변경 없이 계속 작동합니다.

이러한 필드를 수정하려면 다음 단계를 수행합니다.

1. [Adobe 계정 로그인](https://accounts.magento.cloud)에서 계정에 액세스하세요.
1. **[!UICONTROL Account Settings]** 탭을 클릭합니다.
1. *새 암호 만들기* 확인란을 선택하십시오.
1. 필요한 사항을 변경하고 *저장*&#x200B;을 클릭합니다.

>[!NOTE]
>
>암호는 변경되지 않습니다.

## 수정할 수 없는 사항

1. **[!UICONTROL Password]**:
암호를 변경하려면 [Adobe 암호 재설정](https://account.adobe.com/)을 방문하세요. 이 프로필은 계정/전자 메일 주소에 연결되어 있습니다.

1. **[!UICONTROL Email Address]**:
이 필드를 수정하는 것은 개인의 상황에 따라 다릅니다.

현재 계정의 소유권을 새 소유자 또는 다른 이메일 주소로 전송해야 하는 경우 계정과 연결된 기본 사용자 이메일을 업데이트해야 합니다.

다음을 참조하세요. [https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en)
