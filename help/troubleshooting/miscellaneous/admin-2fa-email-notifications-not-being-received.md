---
title: 관리자 2FA 이메일 알림이 수신되지 않음
description: 이 문서에서는 클라우드 인프라의 Adobe Commerce에서 관리자 액세스 보안을 강화하기 위해 2단계 인증(2FA)을 설정한 후 설정 완료 지침이 포함된 이메일을 받지 못하는 경우의 문제 해결을 제공합니다.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 9eaea028886e74fc06c9516801919cd7f650f98c
workflow-type: tm+mt
source-wordcount: '449'
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

스팸 폴더에서 이메일을 확인합니다.

이메일이 스팸 폴더에 표시된 경우 도메인의 이메일 인증이 SendGrid를 통한 아웃바운드 게재에 대해 완전히 구성되지 않을 수 있습니다.

Adobe에서 관리하는 SendGrid 서비스를 사용하는 경우:

SendGrid를 사용하여 전송 도메인을 인증하도록 요청하는 [지원 티켓을 제출](https://experienceleague.adobe.com/home?lang=ko&support-tab=home#support)&#x200B;(*흰색 레이블*이라고도 함).
이 프로세스에는 DNS 레코드(DKIM 및 SPF)를 추가하여 SendGrid가 도메인을 대신하여 이메일을 보내도록 승인하는 작업이 포함되며, 이렇게 하면 이메일이 스팸 폴더가 아닌 받은 편지함으로 배달될 가능성이 높아집니다.

고유한 SendGrid 계정을 사용하는 경우:

SendGrid 계정 대시보드 내에서 직접 도메인 인증 설정을 관리할 책임이 있습니다. 자세한 내용은 SendGrid 설명서의 [도메인 인증을 설정하는 방법](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/how-to-set-up-domain-authentication)을 참조하십시오.

>[!NOTE]
>
>일부 고객은 이메일 전달성 및 규정 준수(예: HIPAA 요구 사항)를 완벽하게 제어하기 위해 별도로 프로비저닝된 SendGrid 서비스를 사용하도록 선택할 수 있습니다. 사용 중인 SendGrid 서비스 유형(Adobe 관리 및 자체 관리)에 따라 올바른 문제 해결 단계를 따르고 있는지 확인합니다.


## 관련 읽기

* 개발자 설명서에서 [SendGrid](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/project/sendgrid)
