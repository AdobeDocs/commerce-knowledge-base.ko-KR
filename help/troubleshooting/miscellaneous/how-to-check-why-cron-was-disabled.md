---
title: ' [!DNL cron] 이(가) 비활성화된 이유 확인 방법'
description: 이 문서에서는 클라우드 인프라 제품에서 Adobe Commerce의 cron 관련 문제에 대한 문제 해결 솔루션을 제공합니다.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# [!DNL cron]이(가) 비활성화된 이유를 확인하는 방법

이 문서에서는 클라우드 인프라 제품에 대한 Adobe Commerce의 [!DNL cron] 문제에 대한 문제 해결 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

## 다음은 [!DNL cron] 문제의 증상입니다.

[!DNL cron]이(가) 실행되고 있지 않습니다.
예를 들어 `app/etc/env.php` 파일에 다음 줄이 표시됩니다.

```'cron' =>
  array (
    'enabled' => 0
  ),
```

배열이 비어 있으면 [!DNL cron]이(가) **enabled**&#x200B;입니다.

```'cron' =>
  array (
  ),
```

## 원인

[!DNL cron]이(가) 현재 활성화되지 않은 이유는 다음과 같습니다.

1. [!DNL OpCache] 설정이 누락되어 [!DNL cron]이(가) 비활성화되었습니다.
1. 인프라 팀이 [!DNL cron]을(를) 비활성화했습니다. 그 결과 사이트의 성능이 떨어졌거나 다운이 발생했기 때문입니다.
1. 배포가 실패했기 때문에 [!DNL cron]을(를) 다시 사용할 수 없습니다.

문제에 대한 해결 방법은 다음 섹션 중 하나를 참조하십시오.

## 솔루션

### 누락된 [!DNL OpCache] 설정에 대한 솔루션 {#solution-missed-opcache-settings}

Commerce 기술 자료에서 [[!DNL Cron] 잘못 구성되었거나 누락되어 중지됨 [!DNL OpCache] 설정](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings)을(를) 참조하십시오.

### 인프라 팀이 비활성화한 솔루션 {#solution-disabled-by-infrastructure-team}

1. 사이트가 다운되었거나 응답하지 않는 이전 지원 티켓을 확인합니다.
1. 그런 다음 인프라 팀이 이를 비활성화했음을 표시했는지 확인합니다.
1. 인프라 팀이 제기한 문제/문제를 해결했는지 확인합니다.
1. [!DNL cron]을(를) 다시 사용하도록 설정하고 인프라 팀이 표시한 문제를 어떻게 해결했는지 설명하는 추가 지원이 필요한 경우 [지원 요청](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets)을 제출하십시오.

### 배포용 솔루션 실패 {#solution-deployment-failed}

배포 로그를 확인합니다.

* Commerce on Cloud Infrastructure 안내서의 [로그 보기 및 관리](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations).
* [Commerce 기술 자료에서 Cloud UI에 *`log snipped`* 오류가 있는 경우 배포 로그를 확인](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)합니다.

1. `setup:upgrade` 단계에서 배포가 실패한 경우 [!DNL cron]이(가) 다시 활성화되지 않습니다.
예를 들어 배포 로그에 다음 줄이 표시됩니다.

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. 그렇지 않으면 다른 단계에서 배포가 실패했을 수 있습니다. 배포 로그를 확인하고 두 행이 모두 표시되는지 확인합니다(아래 예). 로그에 이와 유사한 두 줄이 모두 표시되지 않으면 [!DNL cron]이(가) 다시 활성화되지 않은 것입니다.

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

추가 지원이 필요한 경우 **[지원 요청을 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets)합니다.**
