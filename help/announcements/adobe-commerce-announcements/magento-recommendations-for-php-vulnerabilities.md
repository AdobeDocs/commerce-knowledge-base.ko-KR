---
title: PHP 취약성용 Adobe Commerce Recommendations
description: 9월 3일, 다중 주 정보 공유 및 분석 센터(MS-ISAC)는 임의의 코드 실행을 허용할 수 있는 여러 취약점과 관련된 경고와, PHP를 사용하는 모든 사이트가 최신 PHP 버전으로 즉시 업데이트해야 한다는 권장 사항을 발표했습니다([전체 경고는 여기에서 사용 가능](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# PHP 취약성용 Adobe Commerce Recommendations

9월 3일, 다중 상태 정보 공유 및 분석 센터(MS-ISAC)는 임의의 코드 실행을 허용할 수 있는 여러 취약성과 관련된 경고와 PHP를 사용하는 모든 사이트가 가능한 한 최신 PHP 버전으로 업데이트해야 한다는 권장 사항을 발표했습니다([전체 경고는 여기에서 제공](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Adobe Commerce on cloud infrastructure의 경우 48시간 동안 인프라 팀에 통지하지 않으면 서비스 업그레이드를 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 사항이 프로덕션에 적용되기 48시간 전에 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 필요한 서비스 업그레이드에 대해 자세히 설명하고 업그레이드 프로세스를 시작할 시간을 지정하십시오.

Adobe Commerce 사이트에 대한 영향 및 단계는 을 참조하십시오.

**클라우드 제품에서 호스팅된 Adobe Commerce**

클라우드 인프라에서 Adobe Commerce을 사용하는 경우 기술 팀과 함께 언제든지\*부터 Adobe Commerce을 다시 배포하여 업데이트를 활용하십시오. 월말에 이러한 취약성의 결과로 발효될 수 있는 PCI 규정 준수 문제를 방지하려면 판매자가 9월 30일까지 이 재배포를 완료하는 것이 좋습니다.

이 업데이트의 클라우드 사이트 재배포에 대한 추가 참고 사항:

* 사이트에서 여전히 PHP 버전 7.0을 사용하는 경우 이러한 보안 업데이트를 활용하려면 먼저 지원되는 PHP 버전으로 업그레이드한 후 다시 배포해야 합니다.
* 2.1.x/2.2.x의 경우 PHP 업그레이드에 대한 자세한 내용은 [여기](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=ko)에서 확인할 수 있습니다.

\* *이 문서와 메시지의 이전 버전은 9월 19일에 명시되었지만, 우리 팀은 일정보다 빨리 작업을 완료했습니다.*

**다른 모든 호스팅 솔루션의 Adobe Commerce**

Adobe Commerce은 PHP에 의존하므로 Adobe Commerce을 사용하는 모든 판매자는 호스팅 공급자와 함께 PHP에 필요한 업데이트를 검토하는 것이 좋습니다. 또한 월말에 이러한 취약성의 결과로 시행될 수 있는 PCI 규정 준수 문제를 방지하기 위해 판매자가 9월 30일까지 이 검토와 업데이트를 완료할 것을 권장합니다.

다른 호스팅 솔루션에서 Adobe Commerce에 대한 몇 가지 추가 세부 정보를 참고하십시오.

* 7.1 이전 PHP 버전을 활용하는 Adobe Commerce 버전 2.0 또는 1.x에는 사용 가능한 공식 PHP 패치가 없습니다. 권장되는 경로는 PHP를 지원되는 PHP 버전으로 업그레이드하는 것입니다.

경고에 따라 이 취약성에 대해 권장되는 패치는 다음과 같습니다.

* PHP 7.1: [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

PHP 및 최근 릴리스에 대한 자세한 내용을 보려면 [PHP 사이트](https://www.php.net/)를 방문하세요. 보안 모범 사례에 대한 질문이 있거나 자세한 내용을 보려면 [보안 모범 사례 가이드](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf)를 확인하십시오.
