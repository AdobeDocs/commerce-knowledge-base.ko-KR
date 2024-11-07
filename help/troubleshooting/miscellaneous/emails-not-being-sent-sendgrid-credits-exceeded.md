---
title: Adobe Commerce에서 SendGrid 크레딧을 초과하면 이메일이 전송되지 않음
description: 이 문서에서는 Adobe Commerce에서 SendGrid 크레딧 제한을 초과하여 이메일이 전송되지 않았을 때 솔루션을 제공합니다.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Adobe Commerce에서 SendGrid 크레딧을 초과하면 이메일이 전송되지 않음

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## 문제

SendGrid 크레딧은 전송 가능한 허용된 이메일 수를 나타냅니다. 통합 및 스테이징 분기에서 매월 12,000개의 이메일만 보낼 수 있습니다. 크레딧은 월초에 갱신되기 때문에 크레딧이 다 떨어지면 갱신을 기다려야 한다.

보낸 사람의 신뢰도가 95% 이상인 한 프로덕션에서 보낼 수 있는 이메일 수에는 엄격한 제한이 없습니다. 이러한 신뢰도는 반송되거나 거부된 이메일 수와 DNS 기반 스팸 레지스트리가 도메인을 잠재적인 스팸 소스로 플래그를 지정했는지 여부에 따라 영향을 받습니다. 프로덕션에서는 하루에 총 12,000개의 이메일이 할당되지만 5일 전에 전송된 평균 이메일 수를 기반으로 해당 수를 연장할 수 있습니다.

## 크레딧이 초과되었는지 확인하는 방법:

Adobe Commerce on cloud infrastructure Pro 플랜 아키텍처: `/var/log/mail.log`을(를) 확인하십시오. 다음과 같은 메시지가 표시될 수 있습니다.

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## 원인

보낼 수 있는 허용된 이메일 수에 제한이 있습니다.

## 솔루션

* 프로덕션 환경에서 이 메시지가 표시되면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하고 위의 메시지를 제공하고 크레딧 증가를 요청하세요.
* 이 메시지가 표시되지 않거나 Adobe Commerce on cloud infrastructure 시작 계획 아키텍처에 있는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하고 `mail.log` 파일이 크레딧이 초과되었음을 나타내지 않습니다.

## 관련 읽기

* 개발자 설명서에서 [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid)
