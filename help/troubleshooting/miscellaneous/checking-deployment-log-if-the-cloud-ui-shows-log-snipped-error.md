---
title: Cloud UI에 "로그 스니핑" 오류가 있는 경우 배포 로그 확인
description: 이 문서에서는 클라우드 프로젝트 UI에서 배포 로그를 보려고 할 때 너무 길어서* 클라우드 인프라 UI의 Adobe Commerce에 *로그가 잘린* 오류 메시지가 표시되는 문제에 대한 해결 방법을 제공합니다.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 846df05668b357b9088bcaf605a75c45ab10f1ae
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 클라우드 UI에 *로그 스니핑* 오류가 있는 경우 배포 로그를 확인하는 중

이 문서에서는 클라우드 프로젝트 UI에서 배포 로그를 보려고 할 때 클라우드 인프라 UI의 Adobe Commerce에 너무 길어서 *로그가 잘린* 오류 메시지가 표시되는 문제에 대한 해결 방법을 제공합니다. ([Adobe Commerce Cloud 콘솔](https://console.adobecommerce.com/)에는 적용되지 않습니다.)

## 영향을 받는 제품

클라우드 인프라의 Adobe Commerce(지원되는 모든 버전)

## 문제

클라우드 프로젝트 UI에서 배포 로그를 보려고 하면 클라우드 인프라 UI의 Adobe Commerce에 다음 오류 메시지가 표시됩니다. *로그가 너무 길어서 스니핑되었습니다*.

## 재현 단계

1. 프로젝트 URL로 이동하여 해당 배포의 **상태**&#x200B;를 클릭합니다.
1. 로그가 너무 길어 UI에 표시되지 않으면 *로그가 너무 길어서 스니핑되었습니다*.

## 원인

UI에 표시되는 로그는 사실 소스로 간주해서는 안 됩니다. 특히 배포가 성공 상태로 나열된 후 사이트가 응답하지 않거나 제대로 작동하지 않는 경우에 유용합니다. 서버의 로그에서도 확인해야 합니다. 개발자 설명서에서 [로그 보기 및 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)를 참조하십시오.

## 솔루션

1. 로컬 환경에 [Magento 클라우드 CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html)가 설치되어 있는지 확인하십시오.
1. 다음 명령 중 하나를 실행할 수 있습니다.

   ```bash
   magento-cloud act -p <project id> -e <environment>
   ```

   ```bash
   magento-cloud activity:list -p <project id> -e <environment>
   ```

1. 그러면 다음과 유사한 출력이 반환됩니다.

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. 영향을 받는 배포의 활동 ID를 복사한 다음 명령을 실행합니다.

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   실패한 배포의 로그를 검사하는 예제:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## 개발자 설명서의 관련 내용:

* [클라우드 인프라의 Adobe Commerce > 빌드 및 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [클라우드 인프라의 Adobe Commerce > 로그 보기 및 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
