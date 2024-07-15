---
title: 과도한 Ajax 요청으로 인한 성능 문제
description: 이 문서에서는 과도한 Ajax 요청으로 인해 발생하는 알려진 Adobe Commerce 성능 문제에 대한 패치를 제공합니다. 이 문제는 Adobe Commerce 2.3.4에서 해결되었습니다.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# 과도한 Ajax 요청으로 인한 성능 문제

이 문서에서는 과도한 Ajax 요청으로 인해 발생하는 알려진 Adobe Commerce 성능 문제에 대한 패치를 제공합니다. 이 문제는 Adobe Commerce 2.3.4에서 해결되었습니다.

## 문제

Adobe Commerce이 배너 정보 및 고객 정보를 가져오기 위해 중복 [Ajax 요청](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md)을 상점 첫 화면에서 서버로 보낼 수 있습니다. 이러한 Ajax 요청은 특히 높은 로드(대량 및 높은 트래픽) 조건에서 성능에 영향을 줍니다. 따라서 배너 기능을 사용하지 않는 경우 [Adobe Commerce 배너 모듈 출력을 사용하지 않도록 설정](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)하고 패치를 적용하여 고객 정보 검색을 개선하는 것이 좋습니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch 다운로드](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### 호환 가능한 Adobe Commerce 버전

이 패치는 다음 제품 및 버전에 유효합니다.

* 클라우드 인프라의 Adobe Commerce 2.2.9
* Adobe Commerce 온-프레미스 2.2.9

다른 버전의 Adobe Commerce이 있는 경우 최신 2.3.x 릴리스로 업데이트하는 것이 좋습니다. 현재 옵션이 아닌 경우 [Adobe Commerce 지원 팀에 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 버전에 대한 패치를 요청하십시오.

## 패치 적용 방법

지침은 [Adobe에서 제공한 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
