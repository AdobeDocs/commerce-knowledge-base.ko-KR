---
title: 클라우드 인프라 크론 작업에서 중단된 Adobe Commerce을 수동으로 재설정
description: 클라우드 인프라의 Adobe Commerce cron job은 실행을 완료하지 않고, 중단되며, 다른 cron job이 실행되지 않도록 합니다. 이 문서에서는 중단된 cron 작업을 수동으로 재설정하는 방법을 보여 줍니다.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# 클라우드 인프라 크론 작업에서 중단된 Adobe Commerce을 수동으로 재설정

클라우드 인프라의 Adobe Commerce cron job은 실행을 완료하지 않고, 중단되며, 다른 cron job이 실행되지 않도록 합니다. 이 문서에서는 중단된 cron 작업을 수동으로 재설정하는 방법을 보여 줍니다.

이 명령은 주의해서 사용하십시오! 자세한 내용은 지원 기술 자료에서 [cron 작업 재설정](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=ko) 문서를 읽는 것이 좋습니다.

## 단계

>[!INFO]
>
>[ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=ko#v2002.0.4)에서 SSH 액세스를 통해 CLI 명령을 사용하여 Stick cron 작업을 수동으로 재설정할 수 있습니다.

1. [환경에 SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=ko).
1. 다음 명령을 실행하십시오. `./vendor/bin/ece-tools cron:unlock`

## 경고

* 명령은 현재 실행 중인 작업을 포함하여 **모든** cron 작업을 재설정합니다. **예외적인 경우에만 사용**&#x200B;합니다.
* 인덱서가 실행 중일 때는 이 솔루션을 사용하지 마십시오.

## 지원 기술 자료에서 읽어보십시오.

[크론 작업 재설정](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=ko)
