---
title: '''계정이 일시적으로 비활성화됨'' 오류가 발생하여 [!UICONTROL Commerce Admin] 로그인 양식으로 다시 리디렉션합니다.'''
description: '이 문서는 다음 오류 메시지와 함께 로그인 양식으로 다시 리디렉션되는 Commerce 관리자 로그인 문제에 대해 가능한 솔루션을 제공합니다. *"계정이 일시적으로 비활성화되었습니다."* 제안되는 해결 방법은 관리 사용자 데이터베이스 설정을 확인 및 수정하는 것입니다.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# &quot;계정이 일시적으로 비활성화되었습니다&quot; 오류가 발생하여 [!UICONTROL Commerce Admin] 로그인 양식으로 다시 리디렉션합니다.

이 문서에서는 다음 오류 메시지와 함께 로그인 양식으로 다시 리디렉션되는 [!UICONTROL Commerce Admin] 로그인 문제에 대해 가능한 해결 방법을 제공합니다. *&quot;계정이 일시적으로 비활성화되었습니다&quot;*. 제안되는 해결 방법은 관리 사용자 데이터베이스 설정을 확인 및 수정하는 것입니다.

## 영향을 받는 에디션 및 버전:

모든 Adobe Commerce 버전 및 에디션

## 문제

<u>재현 단계</u>:

1. **[!UICONTROL Commerce Admin]** 페이지로 이동합니다.
1. 자격 증명을 입력하고 **로그인**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

[!UICONTROL Commerce Admin]에 로그인됩니다.

<u>실제 결과</u>:

로그인 양식으로 다시 리디렉션되고 다음 오류 메시지가 표시됩니다. *&quot;계정이 일시적으로 비활성화되었습니다. 나중에 다시 시도하십시오.&quot;*

## 솔루션

1. 데이터베이스 백업을 만듭니다.
1. [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)과(와) 같은 데이터베이스 도구를 사용하거나 명령줄에서 수동으로 DB에 액세스합니다. `admin_user` 데이터베이스 테이블에서 관리자 사용자 레코드에 대해 `is_active`이(가) &quot;`1`&quot;(으)로 설정되어 있고 `lock_expires`이(가) `NULL`인지 확인하십시오. 필요한 경우 이러한 값을 재설정합니다.

## 관련 읽기

* [[!UICONTROL Commerce Admin]에 로그인하려고 할 때 오류 없이 로그인 양식으로 다시 리디렉션합니다.](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
