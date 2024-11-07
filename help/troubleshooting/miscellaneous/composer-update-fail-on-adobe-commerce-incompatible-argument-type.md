---
title: 'Adobe Commerce에서 작성기 업데이트 실패: 호환되지 않는 인수 유형'
description: 이 문서에서는 코드 컴파일 문제로 인해 배포가 중단되는 경우에 대한 해결 방법을 제공합니다. 이 문제는 새 버전의 심포니/콘솔 종속성(4.4.27, 4.4.28)에서 발생합니다.
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Adobe Commerce에서 작성기 업데이트 실패: 호환되지 않는 인수 유형

>[!NOTE]
>
>이 문제는 이제 최신 symfony 버전 4.4.29 릴리스에서 수정되었습니다.

이 문서에서는 코드 컴파일 문제로 인해 배포가 중단되는 경우에 대한 해결 방법을 제공합니다. 이 문제는 새 버전의 심포니/콘솔 종속성(4.4.27, 4.4.28)에서 발생합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드) 및 Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* symfony/console 종속성(4.4.27, 4.4.28).

## 문제

새 버전의 symfony/console 종속성(4.4.27, 4.4.28)으로 인해 종속성 컴파일 프로세스가 실패했습니다.

<u>재현 단계</u>:

Adobe Commerce을 설치 또는 업그레이드하거나 작성기 업데이트를 실행할 때 다음 오류 메시지와 함께 실행이 실패합니다.
*호환되지 않는 인수 형식: 필수 형식: int. 실제 형식: 문자열*

## 원인

이 문제는 Adobe Commerce 코어 코드와 버전 4.4.27 및 4.4.28에 릴리스된 최신 &quot;symfony/console&quot; 종속성이 비호환되어 발생합니다.

## 솔루션

새로운 symfony/console 버전 4.2.29가 출시되면 문제가 자동으로 해결됩니다(2021년 8월 예정).

**Adobe Commerce 온-프레미스에서 해결하는 방법:**

Adobe Commerce 온-프레미스 2.4.x

CLI/Terminal에서 다음 명령을 실행합니다.

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

모든 2.3.5+ Adobe Commerce 온-프레미스 판매자는 다음 CLI 명령을 실행해야 합니다.

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**클라우드 인프라에서 Adobe Commerce을 해결하는 방법:**

위의 명령을 실행하거나 7월 29일 목요일에 사용할 수 있는 최신 ECE 도구 버전(ece-tools: 2002.1.7)으로 업그레이드하십시오. 단계는 개발자 설명서에서 [Adobe Commerce용 클라우드 > ece-tools 버전 업데이트](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)를 참조하십시오.

전체 수정 사항은 Adobe Commerce(모든 배포 방법) 2.4.4에서 릴리스됩니다.

## 관련 읽기

* Github: [2021-07-27 작성기 업데이트와 호환되지 않는 인수 유형: 필수 유형: int. 실제 형식: 문자열](https://github.com/magento/magento2/issues/33595)
