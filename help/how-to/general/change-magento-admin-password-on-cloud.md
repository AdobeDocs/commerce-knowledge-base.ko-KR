---
title: 클라우드 인프라에서 Adobe Commerce의 관리자 암호 변경
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 44238f6d57458028cb1e2612d45e1e12b3f39916
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# 클라우드 인프라에서 Adobe Commerce의 관리자 암호 변경

## 방법 1: 암호를 잊으셨습니까? (이메일을 통해 재설정)

![login_panel_s.png](assets/login_panel_s.png)

사용 안내서의 [관리자 로그인의 암호 재설정](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html?lang=ko#admin-sign-in)에 있는 단계를 읽어 보십시오.

다음은 중요한 사용 노트입니다.

### 발신 이메일 활성화

**암호 찾기** 양식을 사용하기 전에 [클라우드 콘솔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=ko)을 사용하여 [발신 전자 메일을 사용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html?lang=ko)하세요. 이는 통합 환경 및 샌드박스 프로젝트에만 적용됩니다.

송신 이메일이 Pro 프로덕션 또는 스테이징에서 실제로 비활성화된 경우(SendGrid에서 이메일을 선택하지 않은 경우) [클라우드 콘솔에서 이메일 활성화](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/project/outgoing-emails#enable-emails-in-the-cli)를 선택하여 확인할 수 있습니다. 문제가 지속되면 Adobe [지원 티켓](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)을 제출할 수 있습니다.

### 정크 메일 폴더 확인

암호 재설정 링크가 있는 메시지를 찾을 수 없는 경우 *정크 메일* 폴더를 확인하세요. 전자 메일 이름은 *관리자 사용자 이름에 대한 암호 재설정 확인*&#x200B;입니다.

## 방법 2: 새 관리자 추가

기존 사용자의 암호를 복원하거나 재설정할 수 없는 경우에는 새 관리 사용자를 만들고 이 사용자의 암호를 설정할 수 있습니다. 이렇게 하려면 다음 단계를 수행합니다.

1. [SSH를 사용하여 원격 환경에 로그인합니다](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=ko).
1. 다음 명령을 실행합니다. `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
