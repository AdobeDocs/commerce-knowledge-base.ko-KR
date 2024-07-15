---
title: 클라우드 인프라에서 Adobe Commerce의 관리자 암호 변경
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# 클라우드 인프라에서 Adobe Commerce의 관리자 암호 변경

## 방법 1: 암호를 잊으셨습니까? (이메일을 통해 재설정)

![login_panel_s.png](assets/login_panel_s.png)

사용 안내서의 [관리자 로그인의 암호 재설정](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in)에 있는 단계를 읽어 보십시오.

다음은 중요한 사용 노트입니다.

### 발신 이메일 활성화

**암호를 잊으셨습니까** 양식을 사용하기 전에 [클라우드 콘솔을 사용하여 [발신 전자 메일을 사용하도록 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html)하십시오](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### 정크 메일 폴더 확인

암호 재설정 링크가 있는 메시지를 찾을 수 없는 경우 *정크 메일* 폴더를 확인하세요. 전자 메일 이름은 *관리자 사용자 이름에 대한 암호 재설정 확인*&#x200B;입니다.

## 방법 2: 새 관리자 추가

기존 사용자의 암호를 복원하거나 재설정할 수 없는 경우에는 새 관리 사용자를 만들고 이 사용자의 암호를 설정할 수 있습니다. 이렇게 하려면 다음 단계를 수행합니다.

1. [SSH를 사용하여 원격 환경에 로그인합니다](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 다음 명령을 실행합니다. `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
