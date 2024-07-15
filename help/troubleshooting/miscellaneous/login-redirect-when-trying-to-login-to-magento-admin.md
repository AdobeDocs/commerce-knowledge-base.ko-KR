---
title: Commerce 관리자에 로그인할 때 로그인 리디렉션
description: 이 문서에서는 관리자에게 로그인하려고 할 때 로그인 양식으로 다시 리디렉션되고 오류 메시지가 표시되지 않는 Commerce 관리자 로그인 문제에 대한 가능한 해결 방법을 제공합니다. 여기에는 서버 시간대 설정을 수정하고 Adobe Commerce에서 쿠키 설정을 지우는 작업이 포함됩니다.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Commerce 관리자에 로그인할 때 로그인 리디렉션

이 문서에서는 관리자에게 로그인하려고 할 때 로그인 양식으로 다시 리디렉션되고 오류 메시지가 표시되지 않는 Commerce 관리자 로그인 문제에 대한 가능한 해결 방법을 제공합니다. 여기에는 서버 시간대 설정을 수정하고 Adobe Commerce에서 쿠키 설정을 지우는 작업이 포함됩니다.

## 영향을 받는 에디션 및 버전:

모든 Adobe Commerce 버전 및 에디션.

## 문제

<u>재현 단계</u>:

1. Commerce 관리 페이지로 이동합니다.
1. 자격 증명을 입력하고 로그인 을 클릭합니다.

<u>예상 결과</u>:

Commerce 관리자에 로그인됩니다.

<u>실제 결과</u>:

오류 메시지가 없는 로그인 양식으로 다시 리디렉션됩니다.

## 원인

이 문제에 대해 두 가지 가능한 이유가 있습니다.

* 브라우저 수준에서 설정된 시간대가 올바르지 않습니다(실제 라이프타임이 아직 만료되지 않았더라도 관리 세션이 만료된 것으로 간주됨).
* 잘못된 쿠키 설정으로 인해 설정된 세션이 Adobe Commerce에서 사용되지 않습니다.

각 사례의 솔루션에 대해서는 다음 단락을 참조하십시오.

## 솔루션

### 관리 세션 수명 문제

다른 브라우저를 사용하고 1시간 미만인 경우 관리 세션 수명을 늘리십시오.

관리 세션 수명을 늘리려면 다음 단계를 수행합니다.

1. 데이터베이스 백업을 만듭니다.
1. [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)과 같은 데이터베이스 도구를 사용하거나 명령줄에서 DB에 수동으로 액세스하여 다음 SQL 쿼리를 실행합니다.

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. 다음 명령을 실행하여 구성 캐시를 정리합니다.

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### 잘못된 쿠키 설정

쿠키 설정 값을 확인하고 지우려면 다음 단계를 수행하십시오.

1. 데이터베이스 백업을 만듭니다.
1. [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)과 같은 데이터베이스 도구를 사용하거나 명령줄에서 DB에 수동으로 액세스하여 다음 SQL 쿼리를 실행합니다.

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. 값의 응답이 비어 있지 않으면 다음을 실행하여 값을 NULL로 설정합니다.

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. 다음 명령을 실행하여 구성 캐시를 정리합니다.

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## 관련 문서

* [지원 기술 자료에서 &quot;귀하의 계정이 일시적으로 비활성화되었습니다&quot; 오류가 있는 관리자 로그인 양식으로 다시 리디렉션합니다](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md).
* [지원 기술 자료에서 &quot;현재 세션이 만료되었습니다&quot; 오류가 발생한 관리자 로그인 양식으로 다시 리디렉션합니다](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md).
