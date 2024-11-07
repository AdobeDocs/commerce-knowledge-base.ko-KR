---
title: Adobe Commerce용 업그레이드 호환성 도구 1.1.0
description: 업그레이드 호환성 도구 1.1.0은 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 심각한 오류, 문제 및 경고 목록을 반환합니다.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Adobe Commerce용 업그레이드 호환성 도구 1.1.0

업그레이드 호환성 도구 1.1.0은 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 심각한 오류, 문제 및 경고 목록을 반환합니다.

## UCT 1.1.0의 새로운 기능

업그레이드 호환성 도구 1.1.0은 다음을 포함하여 상당한 개선 사항을 제공합니다.

* **핵심 파일 수정 사항 확인**: Adobe은 핵심 제품 코드를 사용자 지정하지 않는 것이 좋습니다. 이 릴리스에서는 고객 및 파트너가 핵심 코드에 대한 수정 사항을 식별할 수 있는 체크포인트를 추가하여 수정 사항의 영향을 조기에 신속하게 이해할 수 있습니다. 개발 프로세스에 이 도구를 추가하면 파트너와 판매자가 문제를 사전에 파악하여 향후 업그레이드 시 문제를 방지하고 TCO(총 소유 비용)를 절감할 수 있습니다.
* **JSON 파일로 보고서 내보내기**: 이 개선 사항은 커뮤니티의 피드백에 따라 구현되었습니다. 이제 도구를 실행하면 식별된 모든 문제의 세부 정보가 JSON 파일로 내보내지므로 사용자가 도구를 다시 실행하지 않고도 결과를 읽고 공유하고 관리할 수 있습니다.
* **향상된 VBE 유효성 검사**: VBE(공급업체 번들 확장 프로그램)는 Adobe Commerce 코어 코드에 속하지 않지만 Adobe에서 테스트하고 지원합니다. 이 업데이트를 통해 이제 코어 코드에 사용하는 것과 동일한 접근 방식을 사용하여 VBE의 유효성을 검사합니다. 이 개선 사항은 사용자가 맞춤화 및 핵심 코드/VBE와 관련된 문제를 명확하게 이해하는 데 도움이 됩니다.
* **오류 코드 제공**: 사용자가 업그레이드 중에 문제를 식별하고 이해하고 해결하는 데 도움이 되는 오류 코드를 도입했습니다. 오류 및 경고 메시지는 명확한 설명과 제안 해결 방법을 제공합니다.
* **중요한 문제만 나열할 가능성**: 이 경우 사용자는 중요한 문제에만 집중할 수 있으며 업그레이드하는 동안 문제가 발생합니다.
* **두 버전 간의 델타 문제**: 커뮤니티 회원이 이 개선 사항을 제안하면 UCT 사용자는 두 버전 간의 문제를 델타하여 업그레이드할 대상 버전에 대해 소개된 새로운 문제에만 집중할 수 있습니다.

## 도구는 어떤 버전을 비교할 수 있습니까?

도구를 사용하여 모든 2.x 버전을 비교할 수 있습니다.

## 업그레이드 호환성 도구 1.1.0은 누가 사용할 수 있습니까?

Adobe Commerce 고객.

## 업그레이드 호환성 도구 1.1.0 설치

설치 단계는 개발자 설명서에서 Adobe Commerce: [호환성 도구 업그레이드 > 설치](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run)를 참조하십시오. 도구를 사용하기 위한 필수 구성 요소는 개발자 설명서에서 Adobe Commerce: [호환성 도구 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/prerequisites)를 참조하십시오.

## 각 호 옆에 있는 번호는 몇 번인가요?

업그레이드 호환성 도구를 실행하는 동안 발생할 수 있는 오류에 대한 정보를 제공하는 오류 메시지 참조입니다.

업그레이드 호환성 도구 오류 메시지는 수준(심각한 문제, 오류 및 경고)과 유형(코어 코드, 사용자 지정 코드 및 GraphQL 스키마)별로 분류됩니다. 각 유형에는 다음 정보가 포함됩니다.

* 오류 코드: Adobe Commerce이 오류 메시지에 대해 할당한 식별자입니다.
* 오류 설명: 오류의 원인을 요약하는 설명입니다.
* 오류 제안 작업: 해당하는 경우 오류를 해결하고 해결하기 위한 지침을 제공합니다.
* 코드는 [오류 메시지 참조 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/reporting/error-messages)에 나열되고 설명되어 있습니다.

## 도구에 대한 피드백을 어디에서 공유할 수 있습니까?

[#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) Slack 채널에서 UCT 팀에 문의할 수 있습니다. 도구를 개선하기 위해 여러분의 의견과 제안을 받을 수 있기를 바랍니다.

## 관련 읽기

* Adobe Commerce 블로그: [업그레이드 호환성 도구 소개(Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: 개발자 설명서에서 [호환성 도구 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview).
