---
title: PHP 버전 준비 확인 문제
description: 이 문서에서는 웹 설치 마법사를 사용하여 Adobe Commerce 온프레미스에 설치/업그레이드할 때 발생할 수 있는 PHP 버전 문제에 대한 해결 방법에 대해 설명합니다.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# PHP 버전 준비 확인 문제

이 문서에서는 웹 설치 마법사를 사용하여 Adobe Commerce 온프레미스에 설치/업그레이드할 때 발생할 수 있는 PHP 버전 문제에 대한 해결 방법에 대해 설명합니다.

>[!WARNING]
>
>클라우드 인프라의 Adobe Commerce에서 서비스 업그레이드는 인프라 팀에 48시간 내에 통지하지 않으면 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 사항이 프로덕션에 적용되기 48시간 전에 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 필요한 서비스 업그레이드에 대해 자세히 설명하고 업그레이드 프로세스를 시작할 시간을 지정하십시오.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## 지원되지 않는 PHP 버전

### 문제

지원되지 않는 PHP 버전을 사용하고 있으므로 검사가 실패합니다.

### 솔루션

이 문제를 해결하려면 개발자 설명서 [2.3.x 시스템 요구 사항](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) 및 [2.2.x 시스템 요구 사항](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)에 나열된 지원되는 버전 중 하나를 사용하십시오.

## PHP 준비 검사가 표시되지 않음

### 문제

다음 그림과 같이 PHP 준비 검사에는 PHP 버전이 표시되지 않습니다.
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### 솔루션

이는 잘못된 cron job setup의 증상입니다. 자세한 내용은 개발자 설명서에서 [cron 작업 설정](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration)을 참조하십시오.

## 잘못된 PHP 버전

### 문제

검사 결과에 잘못된 PHP 버전이 표시됩니다. 일반적으로 여러 PHP 버전이 설치된 고급 사용자에게만 발생합니다. 경우에 따라 준비 검사가 실패하고, 다른 경우에는 통과될 수 있습니다.

준비 검사에서 보고된 PHP 버전이 올바르지 않으면 PHP CLI와 웹 서버 플러그인 사이에 PHP 버전이 일치하지 않기 때문입니다. Adobe Commerce에서는 CLI(cron을 실행함)와 웹 서버(Commerce 관리, 구성 요소 관리자 및 시스템 업그레이드를 실행함) 모두에 PHP *한 버전*&#x200B;을 사용해야 합니다.

### 솔루션

이 문제가 있는 경우 시스템에 여러 버전의 PHP를 설치한 고급 사용자라고 가정합니다.

문제를 해결하려면 다음을 시도해 보십시오.

* 웹 서버 또는 php-fm을 다시 시작합니다.
* `$PATH` 환경 변수에서 PHP에 대한 여러 경로를 확인하십시오.
* `which php` 명령을 사용하여 경로에서 첫 번째 PHP 실행 파일을 찾습니다. 올바르지 않으면 제거하거나 올바른 PHP 버전에 대한 symlink를 만드십시오.
* [`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software) 페이지를 사용하여 자세한 정보를 수집하십시오.
* 개발자 설명서에서 시스템 요구 사항에 따라 지원되는 PHP 버전을 실행하고 있는지 확인하십시오.
   * [Adobe Commerce 시스템 요구 사항](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
* 개발자 설명서에서 [PHP 구성 옵션](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#php-settings)에 설명된 대로 PHP 명령줄과 PHP 웹 서버 플러그인에 대해 동일한 PHP 설정을 설정합니다.
