---
title: 관리자 2FA 이메일 알림이 수신되지 않음
description: 이 문서에서는 클라우드 인프라의 Adobe Commerce에서 관리자 액세스 보안을 강화하기 위해 2단계 인증(2FA)을 설정한 후 설정 완료 지침이 포함된 이메일을 받지 못하는 경우의 문제 해결을 제공합니다.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 435a545adcf2a1d6b023abaec55c4b73e942ee1a
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# 관리자 2FA 이메일 알림이 수신되지 않음


## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

관리자 액세스 보안을 강화하기 위해 2단계 인증을 설정했지만 설정 완료에 대한 지침이 포함된 이메일이 수신되지 않습니다.

## 원인

발신자 이메일을 제대로 구성하지 않았거나 도메인이 SendGrid에 흰색 레이블이 지정되지 않은 경우 이메일이 Spam 폴더로 끝났을 수 있습니다.

## 문제 해결

### 1단계: 스팸 폴더 확인

1. 스팸 폴더에 이메일이 표시되지 않은 경우 이 Mysql 쿼리를 실행하여 이메일 주소가 구성되었는지 확인합니다.

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * 결과를 반환하지 않으면 발신자 주소가 구성되지 않은 것입니다.
관리자에 대한 액세스 권한이 없으므로 데이터베이스에 구성을 삽입해야 합니다. 적절한 이메일 주소를 연결하고 MySQL 문을 실행합니다.

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * 결과를 반환하면 **2단계**&#x200B;로 진행합니다.

1. 이메일이 스팸 폴더에 표시된 경우 해당 이메일의 링크를 클릭합니다. 링크가 만료된 경우 다시 로그인하여 프로세스를 반복하십시오.
1. 액세스 권한이 부여되면 **스토어** > **구성** > **일반** > **전자 메일 주소 저장**&#x200B;으로 이동하여 전자 메일 주소를 구성하십시오.

### 2단계: 이메일 주소가 제대로 구성된 경우 환경에 SSH를 넣고 다음 명령을 실행합니다.

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

스팸 폴더에서 이메일을 확인합니다. 전자 메일이 여기에 표시되면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login)하여 SendGrid에서 흰색 레이블이 지정되도록 도메인을 요청합니다.

## 관련 읽기

* 개발자 설명서에서 [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html)
