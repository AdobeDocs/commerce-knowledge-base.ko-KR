---
title: 클라우드 인프라 업사이징에서 임시 Adobe Commerce을 요청하는 방법
description: 조직에서 트래픽이 많을 것으로 예상하는 온라인 이벤트를 계획하고 있거나, 갑자기 사이트가 높은 트래픽 이벤트를 받는 경우 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 제출하여 Adobe Commerce on cloud infrastructure store에 대한 임시 클라우드 용량을 요청할 수 있습니다.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# 클라우드 인프라 업사이징에서 임시 Adobe Commerce을 요청하는 방법

조직에서 트래픽이 많을 것으로 예상하는 온라인 이벤트를 계획하고 있거나, 갑자기 사이트가 높은 트래픽 이벤트를 받고 있는 경우 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 제출하여 클라우드 인프라 스토어에서 Adobe Commerce에 대한 임시 클라우드 용량을 추가로 요청할 수 있습니다.

>[!NOTE]
>
>비긴급 upsize 요청에 48 업무 시간 알림이 필요합니다. 사이트가 완전히 작동하지 않거나 예상보다 훨씬 높은 트래픽을 받고 성능이 심각하게 저하되지 않는 한 프로모션 캠페인에 대한 업사이드는 긴급 상황으로 간주되지 않습니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 높은 트래픽 이벤트를 식별하는 방법

New Relic 경고에서 기준 경고 조건을 사용하여 데이터의 비헤이비어에 맞게 조정되는 임계값을 정의할 수 있습니다.

기준 경고 는 다음과 같은 경고 조건을 만드는 데 유용합니다.

* 데이터가 비정상적으로 작동할 때만 알립니다.
* 일별 또는 주별 트렌드를 포함하여 변화하는 데이터 및 트렌드에 동적으로 적응할 수 있습니다.

또한 알려진 비헤이비어가 없을 경우 새 애플리케이션에서 기준선 경고 기능이 제대로 작동합니다.

이 링크를 따라 New Relic [Intelligence가 적용된 예외 항목 탐지](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/)에 대해 자세히 알아보십시오.

트래픽이 많은 이벤트를 알리는 경고 알림을 받는 경우 [지원 티켓을 제출](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket)하여 용량을 추가로 요청해야 할 수 있습니다. 아래 단계를 수행합니다.

## 사이트 성능을 모니터링하는 방법

Adobe은 클라우드 인프라의 Adobe Commerce Pro 계획 아키텍처 및 클라우드 인프라의 Adobe Commerce Starter 계획 아키텍처 프로덕션 환경에서 다음 주요 성능 지표를 추적할 수 있도록 New Relic 경고 정책 세트를 제공합니다.

* [Apdex 점수](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* 오류율
* 디스크 공간(Pro 아키텍처 프로덕션 환경에서만 사용 가능)

업계 모범 사례를 기반으로 이러한 정책은 성능에 영향을 주는 경고 및 중요 조건에 대한 임계값을 설정합니다. 경고 임계값을 트리거하는 인프라 또는 애플리케이션 문제가 사이트에 발생하면 New Relic에서 사전 예방적으로 문제를 해결할 수 있도록 경고 알림을 보냅니다. 이러한 정책을 사용하려면 경고 메시지를 수신하도록 알림 채널을 구성해야 합니다.

[성능 기반 경고를 구성](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts)하는 방법을 알아보려면 이 링크를 따르십시오.

## 임시 업사이징을 요청하는 단계

임시 추가 클라우드 용량을 요청하려면 아래 단계에 따라 [지원 티켓](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket)을 제출하십시오.

다음 정보를 입력한 후 Adobe Commerce 지원 센터에서 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket):

>[!NOTE]
>
>*휴일 서지 요청* 선택은 10월과 12월 사이의 옵션입니다.

1. 지원을 요청하는 Adobe Commerce 제품을 선택하십시오.
1. 처음 네 개의 (제품, 조직, 구현 유형, 주제) 필드를 완료합니다.
1. **연락처 이유** 드롭다운에서 *Adobe Commerce 클라우드 인프라*&#x200B;을(를) 선택합니다.
1. **Adobe Commerce 인프라 연락처 이유** 드롭다운 옵션에서 *휴일 서지 용량 요청*&#x200B;을 선택합니다. 임시 추가 클라우드 용량 요청에 대한 48시간(영업시간 기준) 알림을 요청하는 팝업 메시지에서 **확인**&#x200B;을 클릭합니다.
1. 필수 필드 **시작 날짜 크기 조정** 및 **종료 날짜 크기 조정**&#x200B;의 날짜를 선택하십시오. 기본 설정 **크기 조정 시작 시간**&#x200B;도 필수 필드입니다.
1. 다음 네 개의 필드를 완료합니다.
1. **설명** 필드에 크기에 대한 추가 정보가 있으면 여기에 입력하십시오. 더 큰 크기를 요청하지 않는 경우, 다음 더 큰 환경 용량으로 업사이징합니다. Surge 요청은 기본적으로 현재 크기에서 다음 큰 크기로 설정됩니다. 추가 용량이 필요한 경우 **설명** 필드에 을 표시하십시오. 늘어난 용량은 계약된 Surge Days 또는 vCPU Days에서 공제됩니다. 일반적인 용량 증가 기간은 5일이지만, 더 많거나 더 적은 날짜가 필요한 경우 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)에 이 기간을 표시하십시오.

>[!NOTE]
>
>업사이즈가 예약되면 자동화된 시스템에서 클라우드 인스턴스의 크기를 조정합니다. 절차가 완료되면 티켓 알림을 받지 못할 수 있습니다. Observation for Adobe Commerce 도구를 사용하여 AWS 또는 Azure 인스턴스 유형을 보고 [변경 내용을 확인](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)할 수 있습니다.

## 업사이징 내역 보기

**CSM(Customer Success Manager)**에 정보를 요청하여 요청된 크기 조정 내역을 볼 수 있습니다.
각 크기 조정 요청에 대해 다음 정보를 사용할 수 있습니다.

* **크기 시작 날짜**: upsize 요청 날짜.
* **크기 종료 날짜**: 클러스터가 이전 크기로 반환된 날짜입니다.
* **vCPU 크기**: upsize 이후의 클러스터 크기입니다.
* **일 사용**: 클러스터가 업사이징된 상태로 유지되는 기간(일).
* **기간 vCPU**: 사용된 일수만큼 vCPU 크기가 변경되었습니다. 예를 들어 vCPU 크기 192 x 25일은 4,800입니다.


## 관련 읽기

* 사이트 성과를 측정하고 개선하는 방법에 대한 통찰력, 방법 및 예는 지원 기술 자료에서 다음 심층 문서를 참조하십시오.
   * [클라우드에서 Adobe Commerce에 대한 CPU 할당 계산](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [클라우드에서 Adobe Commerce에 대해 호스트 인스턴스의 업사이징이 필요한지 확인](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [클라우드에서 Adobe Commerce에 대한 호스트의 CPU 구성 확인](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* 중단을 식별하는 방법에 대한 자세한 내용은 지원 기술 자료에서 [클라우드에서 Adobe Commerce에 대한 중단 식별 및 측정](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)을 참조하세요.
* 용량 증가를 활용할 필요가 없도록 사이트 성능을 개선하는 방법에 대한 자세한 내용은 개발자 설명서에서 다음 문서를 참조하십시오.
   * [이미지 크기 조정](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [전체 페이지 캐싱](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
