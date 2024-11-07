---
title: Adobe Commerce [!DNL crons] 개입 없이 비활성화됨
description: 이 문서를 사용하여  [!DNL crons] 이(가) 개입 없이 비활성화되는 문제를 해결할 수 있습니다.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# 개입 없이 Adobe Commerce 크론이 비활성화됨

이 문서에서는 개입 없이 [!DNL crons]을(를) 사용하지 않도록 설정하는 경우에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 문제

배포 후 [!DNL crons]을(를) 사용할 수 없습니다.

<u>재현 단계</u>:

배포.

<u>예상 결과</u>:

[!DNL crons]이(가) 실행 중입니다.

<u>실제 결과</u>:

배포 후 [!DNL crons]을(를) 사용할 수 없습니다.

## 원인

[!DNL OPcache] 설정에 문제가 있습니다.

## 솔루션

[!DNL ECE Tools]을(를) 최신 버전 [2002.1.13](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113)(으)로 업그레이드하십시오.

## 관련 읽기

* 지원 기술 자료에서 [느린 성능, 느리고 긴 실행 [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html).
* [[!DNL Cron] 작업은 다른 그룹의 작업을 잠그고](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en)있습니다.
* [[!DNL Cron] 작업이 지원 기술 자료에서 &quot;실행 중&quot; 상태](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en)에서 중단되었습니다.
