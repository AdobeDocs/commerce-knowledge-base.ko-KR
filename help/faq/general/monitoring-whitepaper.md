---
title: 다음에 대한 모니터링 팩트시트 [!DNL Adobe Commerce on cloud pro infrastructure]
description: 이 문서에서는 Adobe Commerce 인프라 모니터링 및 알림에 대한 정보를 제공합니다.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# 다음에 대한 모니터링 팩트시트 [!DNL Adobe Commerce on cloud pro infrastructure]

이 문서에서는 Adobe Commerce 인프라 모니터링 및 알림에 대한 정보를 제공합니다.

모니터링을 통해 판매자, 시스템 통합업체 및 Adobe 내부 팀이 사이트 가용성 및 디스크 공간 부족 문제를 해결할 수 있습니다.

## 문제 해결 및 해결

Adobe Commerce 인스턴스는 일반적으로 사용자 지정 코드 및 구성을 포함합니다. Adobe은 사용자 지정 코드 및 구성 관련 문제를 지원하거나 해결하지 않습니다. Adobe은 상인이 당사의 지식 기반에서 문제를 해결하고 식별하는 데 도움이 되며 예방 및 해결을 위한 권장 솔루션과 모범 사례를 제공합니다. 판매자와 파트너가 아래 표를 사용하여 모니터링되는 항목과 해결의 책임자를 이해할 것을 권장합니다.

알림이 트리거되면 Adobe Commerce 지원 팀이 문제를 평가합니다. 분류의 일부로 오류 로그 및 기타 리소스가 분석됩니다. 등급 기준, 추가 [!DNL Zendesk] 지원 티켓은 문제를 해결하기 위해 판매자 또는 파트너(사용자 지정 업데이트의 경우) 또는 Adobe의 내부 팀에 생성됩니다.

## Adobe Commerce: 기본 모니터링

아래 이벤트가 모니터링되며 Adobe Commerce 팀은 식별된 문제를 해결하고 전달하는 데 필요한 단계를 수행합니다.

## 사이트 가용성 모니터링

| 사이트 가용성 | 설명 |
|------------|------------|
| **목표 모니터링** | 사이트 가용성을 추적하려면 |
| **계측한 날짜** | 단일 [!DNL URL] 높음을 위해 선택됨 [!DNL SLA]. |
| **설명** | 사이트 가용성은 측정 단위에 대해 구성된 임계값을 기반으로 결정됩니다. 10분 동안 검사가 실패하고 진행 중인 활성 배포가 없는 경우 사이트 중단 알림이 트리거됩니다. |
| **알림 수신자** | 판매자/파트너 및 Adobe. |
| **Adobe에 의한 작업** | Adobe Commerce 인프라에 문제가 있는 경우 평가 및 수정을 담당합니다. |
| **상인별 행동** | 판매자/파트너가 도입한 사용자 지정 코드 또는 변경 사항으로 인해 문제가 발생한 경우 이 문제를 해결할 책임이 있습니다. 문제 해결에 대해서는 다음을 참조하십시오. [사이트 작동 중지 문제 해결사](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## 디스크 공간 모니터링

| 디스크 공간 모니터링 | 설명 |
|------------|------------|
| **목표 모니터링** | 디스크 공간 사용을 추적하려면 |
| **계측한 날짜** | [!DNL MySQL] 디스크 및 미디어 디스크 파티션. |
| **지표** | 호스트에서 사용 가능한 디스크 공간이 매 분마다 모니터링됩니다. 사용 가능한 공간이 5% 또는 2GB만 남아 있으면 경고가 발생합니다. 나머지 여유 공간에서 설정된 임계 임계값은 2% 또는 1GB입니다. |
| **설명** | 알림은 호스트에 대해 사용 가능한 디스크 공간 주위에 구성된 임계값을 기반으로 전송됩니다. 추가 디스크 공간이 관련 마운트에 한 번 자동으로 추가됩니다([!DNL MySQL] 또는 미디어)를 사용하면 사이트 중단을 방지하고, 디스크 공간을 정리하거나, 빠른 디스크 사용량 증가를 유발하는 모든 코드 또는 로그를 식별하고 해결할 수 있습니다. |
| **알림 수신자** | 판매자/파트너 및 Adobe. |
| **Adobe에 의한 작업** | 지원 티켓을 자동으로 높이고 관련 마운트에 추가 디스크 공간을 자동으로 추가합니다([!DNL MySQL] 또는 미디어)를 사용하여 사이트 중단을 방지해야 합니다. |
| **상인별 행동** | 진행 중인 경고 수준의 디스크 공간 경고를 받으려면 다음을 참조하십시오. <ul><li>[[!DNL Managed alerts for Adobe Commerce]: 디스크 경고](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: 디스크 위험 경고](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
