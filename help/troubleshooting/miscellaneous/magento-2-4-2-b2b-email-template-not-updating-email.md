---
title: 'Adobe Commerce 2.4.2 B2B: 이메일 템플릿이 이메일을 업데이트하지 않음'
description: 이 문서에서는 이메일 템플릿의 일부 정보를 업데이트해도 이메일에서 업데이트되지 않는 알려진 Adobe Commerce 2.4.2 B2B 문제에 대해 설명합니다. 이 문제는 고객 정보, 환율, 통화 기호, 이메일 템플릿 변경 등과 같은 이메일 콘텐츠에 영향을 줍니다. 현재 사용할 수 있는 해결책은 없지만 이 문서의 하단에 해결 방법이 있습니다.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: 이메일 템플릿이 이메일을 업데이트하지 않음

이 문서에서는 이메일 템플릿의 일부 정보를 업데이트해도 이메일에서 업데이트되지 않는 알려진 Adobe Commerce 2.4.2 B2B 문제에 대해 설명합니다. 이 문제는 고객 정보, 환율, 통화 기호, 이메일 템플릿 변경 등과 같은 이메일 콘텐츠에 영향을 줍니다. 현재 사용할 수 있는 해결책은 없지만 이 문서의 하단에 해결 방법이 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.2
* Adobe Commerce 클라우드 인프라 2.4.2
* B2B 1.3.1

## 문제

<u>재현 단계</u>:

1. 회사 관리자는 프론트엔드에 PO(구매 주문)를 만듭니다.
1. 자동 승인 이메일을 확인합니다. **고객 이름** / **환율**&#x200B;은(는) 예상 값이어야 합니다.
1. 고객 계정 페이지에서 관리자 및 회사 관리자 이름의 통화 기호(**저장 > 구성 > 통화 설정 > 통화 옵션**)를 변경합니다.
1. 고객 관리자가 관리자에서 다른 PO를 만듭니다.
1. 자동 승인 이메일을 확인합니다.

<u>예상 결과:</u>

고객 이름과 통화 기호는 이메일에서 변경되며, 예상대로 새 값을 갖습니다.

<u>실제 결과</u>:

고객 이름 및 통화 기호는 이메일에서 변경되지 않으며 이전 값을 갖습니다.

## 해결 방법

cron 작업 또는 고객을 수동으로 실행하여 새 정보를 전파하십시오.

## 관련 읽기

* 개발자 설명서에서 [메시지 큐 관리](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues).
