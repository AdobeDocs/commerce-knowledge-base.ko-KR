---
title: '"현재 세션이 만료되었습니다" 오류가 있는 Commerce 관리자 로그인 양식으로 다시 리디렉션합니다.'
description: '''이 문서는 다음 오류 메시지와 함께 로그인 양식으로 다시 리디렉션되는 Commerce 관리자 로그인 문제에 대해 가능한 솔루션을 제공합니다. *"현재 세션이 만료되었습니다"*. 해결 방법에는 서버 시간 설정 문제 확인 및 세션 저장소 설정 변경이 포함됩니다.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# &quot;현재 세션이 만료되었습니다&quot; 오류가 있는 Commerce 관리자 로그인 양식으로 다시 리디렉션합니다.

이 문서에서는 다음 오류 메시지와 함께 로그인 양식으로 다시 리디렉션되는 Commerce 관리자 로그인 문제에 대해 가능한 해결 방법을 제공합니다. *&quot;현재 세션이 만료되었습니다.&quot;*. 해결 방법에는 서버 시간 설정 문제 확인 및 세션 저장소 설정 변경이 포함됩니다.

## 영향을 받는 에디션 및 버전:

모든 Adobe Commerce 버전 및 에디션

## 문제

<u>재현 단계</u>:

1. Commerce 관리 페이지로 이동합니다.
1. 자격 증명을 입력하고 로그인 을 클릭합니다.

<u>예상 결과</u>:

Commerce 관리자에 로그인됩니다.

<u>실제 결과</u>:

다음 오류 메시지가 표시된 로그인 양식으로 다시 리디렉션됩니다. *&quot;현재 세션이 만료되었습니다.&quot;*.

## 원인

이 문제에 대해 두 가지 가능한 이유가 있습니다.

* 서버 시간 설정 문제
* 세션 저장소 문제

다음 섹션에서 솔루션을 확인하십시오.

## 솔루션

### 서버 시간 설정 문제 확인

에서 생성된 세션 레코드를 확인합니다. `admin_user_session` 테이블. 다음 값: `created_at` 및/또는 `updated_at` 이(가) 잘못되었습니다. 서버 시간 설정 문제로 인해 발생할 수 있습니다. 서버 시스템 관리자에게 문의하여 확인하십시오. DB의 해당 시간은 기본적으로 UTC로 설정되어 있습니다.

### 세션 저장소 변경

세션 저장소를 변경해 보십시오. 의 정보를 사용합니다. [세션 파일을 찾는 방법](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) 개발자 설명서에서 세션이 저장된 위치를 확인하고 를 편집하여 변경하는 데 필요한 문서 `app/etc/env.php` 파일.

예를 들어 파일 시스템에 세션 저장을 시작하려면 `'session'` 섹션을 다음과 같이 바꿉니다.

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

실행 `bin/magento app:config:import` 구성 데이터를 가져오는 명령입니다.


## 관련 읽기

* [구성 파일에서 데이터 가져오기](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) 개발자 설명서에서
* [Redis 구성](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) 개발자 설명서에서
* [&quot;계정이 일시적으로 비활성화됨&quot; 오류가 표시된 Commerce 관리자 로그인 양식으로 다시 리디렉션합니다.](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) 지원 기술 자료
* [Commerce 관리자에 로그인할 때 오류 없이 로그인 양식으로 다시 리디렉션합니다.](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) 지원 기술 자료
