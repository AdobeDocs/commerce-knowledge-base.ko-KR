---
title: Cloud 2.4.4의 Adobe Commerce OpenSearch로 전환
promoted: true
description: cloud infrastructure 2.4.4의 Adobe Commerce은 7.10 이후 버전의 Elasticsearch을 지원하지 않습니다. **먼저 Adobe Commerce 2.4.4로 업그레이드한 다음 즉시 Elasticsearch에서 OpenSearch 1.2.x로 전환해야 합니다.** Adobe은 Adobe Commerce 2.4.4 GA 릴리스에 가까운 세부 지침을 제공합니다.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Cloud 2.4.4의 Adobe Commerce OpenSearch로 전환

클라우드 인프라 2.4.4의 Adobe Commerce은 7.10 이후 버전의 Elasticsearch을 지원하지 않습니다. **먼저 Adobe Commerce 2.4.4로 업그레이드한 다음 Elasticsearch에서 OpenSearch 1.2.x로 즉시 전환해야 합니다.** Adobe은 Adobe Commerce 2.4.4 GA 릴리스와 가까운 세부 지침을 제공합니다.

>[!NOTE]
>
>전환은 클라우드 공급자에 관계없이 수행되어야 합니다.

Adobe Commerce 온프레미스에서 2022년 3월 패치 릴리스(2.4.4, 2.4.3-p2 및 2.3.7-p3) 모두에서 Elasticsearch 7.16 및 OpenSearch 1.2에 대한 지원을 추가하고 있습니다. 2.4.4에서는 클라우드 인프라의 Adobe Commerce이 기본 검색 엔진으로 OpenSearch로 이동하므로 판매자는 Adobe Commerce 2.4.4 이상으로 업그레이드하기 전에 Elasticsearch 대신 OpenSearch를 사용해야 합니다. Adobe Commerce 온-프레미스 배포가 있는 판매자는 Elasticsearch 또는 OpenSearch를 사용할 수 있습니다. Adobe Commerce은 두 가지를 계속 지원합니다.


## OpenSearch란?

OpenSearch는 Elasticsearch과 키바나의 포크입니다. Elastic.co. 대신 AWS이 유지 관리합니다. 자세한 내용은 GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch)를 검토하십시오.

**버전 간 호환성:**

**클라우드 인프라의 Adobe Commerce에서 Elasticsearch 7.10을 지원합니까?**

**예** - 2022년 1월 중순부터 Adobe Commerce on cloud infrastructure 버전 2.4.3-p1, 2.4.3-p2 및 2.3.7-p3 지원 Elasticsearch 7.10이 시작됩니다.

Adobe Commerce 온프레미스의 경우 Log4j를 완화하려면 최신 7.16.x 버전이 권장됩니다.

## 마이그레이션:

## 판매자는 언제 OpenSearch로 마이그레이션할 수 있습니까?

Adobe Commerce 2.4.4 이후.

그러나 Adobe Commerce 2.4.4로 업그레이드 프로세스를 시작하기 전에 판매자는 Adobe Commerce 2.4.4 또는 OpenSearch로 업그레이드 프로세스를 시작하기 전에 Elasticsearch 7.10을 지원하는 현재 버전의 Adobe Commerce에 있어야 하며 적어도 Elasticsearch에 있어야 합니다.

## 2.4.4에 있지 않은 상인(클라우드 인프라의 Adobe Commerce 및 Adobe Commerce 온프레미스)은 무엇을 할 수 있습니까? 지원되는 버전의 Elasticsearch(7.10, 7.16.1) 또는 OpenSearch로 업그레이드할 수 있습니까? 이렇게 하려면 지원되는 최신 버전(예: 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)에 있어야 합니까?

현재 사용 중인 Adobe Commerce 코어 버전이 Elasticsearch 7.10을 지원하는 경우 이를 사용할 수 있습니다.

버전 호환성에 대해서는 개발자 설명서에서 [시스템 요구 사항](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)을 검토하십시오.

>[!NOTE]
>
>Elasticsearch 7.10은 2022년 5월에 EOL이므로 가능한 한 빨리 Adobe Commerce 2.4.4로 업그레이드할 계획을 세우는 것이 좋습니다.

Adobe 파트너는 Beta 프로그램 [여기](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html)에 등록하여 Elasticsearch 7.16.1 및 OpenSearch 1.1에 대해 테스트된 최신 beta4 코드에 액세스할 수 있습니다.
