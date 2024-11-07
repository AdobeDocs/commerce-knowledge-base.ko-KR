---
title: Adobe Commerce에서 클라우드 분기 재배열
description: 이 문서에서는 올바른 계층에 따라 구성되지 않은 경우 Adobe Commerce에서 클라우드 분기를 다시 정렬하는 데 사용할 수 있는 단계를 제공합니다. 올바른 계층에 구성된 분기가 없는 경우 올바른 상위 분기로 병합할 수 없습니다. 기존 상위 분기로 이동합니다.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce에서 클라우드 분기 재배열

이 문서에서는 올바른 계층에 따라 구성되지 않은 경우 Adobe Commerce에서 클라우드 분기를 다시 정렬하는 데 사용할 수 있는 단계를 제공합니다. 올바른 계층에 구성된 분기가 없는 경우 올바른 상위 분기로 병합할 수 없습니다. 기존 상위 분기로 이동합니다.

## 영향을 받는 제품 및 버전:

* 클라우드 인프라의 Adobe Commerce, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## 클라우드 분기 조직

분기의 올바른 계층 조직은 다음과 같습니다.

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## 잘못된 클라우드 분기 조직에 대한 솔루션

클라우드 분기를 다시 정렬하려면 다음을 수행하십시오.

1. [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) 역할이 있어야 합니다.
1. magento-cloud [!DNL CLI]을(를) 설치합니다(설치하지 않은 경우).
1. 이동해야 하는 분기에 대해 다음 명령을 실행합니다.
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

참고: 새 분기를 만들 때 상위 분기를 지정할 수 있습니다. 단계는 개발자 설명서에서 [분기 만들기를 시작하는 중](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches)을 참조하세요.

`branch <environment-name> <parent-environment-ID>` magento-cloud 환경 명령을 사용하여 새 환경 분기를 만들 수 있습니다.

새 환경 분기를 만들고 활성화하는 데 약간의 추가 시간이 걸릴 수 있습니다.

## 관련 읽기

개발자 설명서에서 [ [!DNL CLI]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches)을(를) 사용하여 분기를 관리합니다.
