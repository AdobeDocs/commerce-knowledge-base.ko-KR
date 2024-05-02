---
title: '[!DNL Advanced Reporting] Adobe Commerce의 404 오류'
description: 이 문서에서는 판매자가 다음에 액세스하려고 할 때 404 오류가 발생하는 경우 Adobe Commerce 문제에 대한 패치를 제공합니다[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). 이 패치를 설치하면 사용자가 액세스할 수 있습니다 [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] Adobe Commerce에서 404 오류

이 문서에서는 판매자가 액세스를 시도할 때 404 오류가 발생하는 Adobe Commerce 문제에 대한 패치를 제공합니다 [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). 이 패치를 설치하면 사용자가 액세스할 수 있습니다 [!DNL Advanced Reporting].

이 패치로 이 문제를 해결할 수 있는지 확인하려면 먼저 다음 명령을 사용하여 로그를 검토하십시오.

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

다음 항목이 표시되면 `Not valid cipher` 오류가 발생했습니다. 첨부된 패치를 적용하십시오.

## 영향을 받는 제품 및 버전

Adobe Commerce 2.2.6

## 문제

판매자가 액세스를 시도하면 404 오류가 발생합니다 [!DNL Advanced Reporting].

## 솔루션

이 문제를 해결하려면 이 문서에 첨부된 패치를 적용하십시오. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다. [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1 다운로드](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## 패치 적용 방법

다음을 참조하십시오 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 설명서를 참조하십시오.

## 첨부 파일
