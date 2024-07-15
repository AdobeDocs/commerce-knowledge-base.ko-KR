---
title: Adobe Commerce cloud infrastructure 2.3.1 이상 업그레이드 후 Elasticsearch 문제
description: 이 문서에서는 Elasticsearch 버전 2.x 및 5.x를 사용하는 경우 클라우드 인프라 버전 2.3.1+의 Adobe Commerce으로 업그레이드한 후 배포하는 동안 발생하는 문제의 수정 사항에 대해 설명합니다.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Adobe Commerce cloud infrastructure 2.3.1 이상 업그레이드 후 Elasticsearch 문제

>[!WARNING]
>
>[MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거됩니다](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). 버전 2.4.0을 설치하기 전에 Elasticsearch 호스트를 설정하고 를 구성해야 합니다. [Elasticsearch 설치 및 구성](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)을 참조하세요.

>[!WARNING]
>
>서비스 업그레이드는 48시간 동안 인프라 팀에 통보하지 않으면 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 사항이 프로덕션에 적용되기 48시간 전에 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 필요한 서비스 업그레이드에 대해 자세히 설명하고 업그레이드 프로세스를 시작할 시간을 지정하십시오.

이 문서에서는 Elasticsearch 버전 2.x 및 5.x를 사용하는 경우 클라우드 인프라 버전 2.3.1+의 Adobe Commerce으로 업그레이드한 후 배포하는 동안 발생하는 문제의 수정 사항에 대해 설명합니다.

## 영향을 받는 제품 및 버전:

* 클라우드 인프라의 Adobe Commerce 2.3.1+
* Elasticsearch 2.x 및 5.x

## 원인

클라우드 인프라(버전 2.3.1 이상)에서 Adobe Commerce으로 업그레이드하고 6.x 이전 버전의 Elasticsearch에 있는 판매자는 배포 시 오류가 발생할 수 있습니다. 이는 Elasticsearch 버전 2.x 및 5.x가 [수명 종료](https://www.elastic.co/support/eol)이고 Adobe Commerce에서 더 이상 지원되지 않기 때문입니다. Elasticsearch 클라이언트가 최신 상태여야 하거나 배포를 실행하면 오류가 트리거될 수 있습니다. 자세한 내용은 개발자 설명서에서 [Elasticsearch 클라이언트 변경](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html)을 참조하세요.

## 문제

배포할 때 Elasticsearch 버전이 호환되지 않음을 나타내는 다음과 유사한 오류 메시지가 표시됩니다. 인프라 계층의 *Elasticsearch 서비스 버전 5.2.2는 Magento 응용 프로그램에서 사용하는 현재 버전의 elasticsearch/elasticsearch module(6.7.0.0)과 호환되지 않습니다.* *Magento 클라우드 인프라의 Elasticsearch 서비스를 버전 6.x로 업그레이드하면 이 문제를 해결할 수 있습니다*. 이 문제의 다른 증상은 이미지 누락 및 환경 내 필터 문제일 수 있습니다.

## 솔루션

>[!WARNING]
>
>공유 환경이 있는 경우 스테이징 및 프로덕션을 업그레이드할 준비가 되었는지 확인하십시오.

이 문제를 해결하려면 Elasticsearch 클라이언트 모듈 및 Elasticsearch 서비스가 권장 최신 버전이어야 합니다.

1. 권장되는 최신 버전의 Elasticsearch 클라이언트 모듈을 사용할 수 있도록 개발자 설명서에서 [Elasticsearch 모듈을 변경](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html)하는 지침을 따르십시오.
1. [지원 티켓을 제출하고](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 스테이징 및 프로덕션에서 Elasticsearch 서비스 업데이트를 6.x로 요청합니다. Elasticsearch 서비스 업그레이드를 완료하는 데 시간이 걸릴 수 있습니다.

## 관련 읽기

* 개발자 설명서에서 [Adobe Commerce 2.3 기술 스택 요구 사항](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html)을 참조하십시오.
* 개발자 설명서에서 [Elasticsearch 서비스를 설정](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html)합니다.
* 개발자 설명서에서 [Elasticsearch 설치 및 구성](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).
* 지원 기술 자료에서 [Elasticsearch이 제대로 설치되었는지 확인](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md).
