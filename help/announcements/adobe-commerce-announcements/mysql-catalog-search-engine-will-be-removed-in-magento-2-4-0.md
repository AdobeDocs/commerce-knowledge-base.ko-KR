---
title: MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거됩니다.
description: Adobe Commerce 온프레미스, Adobe Commerce 온클라우드 인프라 및 Magento Open Source 2.4.0이 향후 몇 개월 내에 출시될 예정입니다. Adobe Commerce 온-프레미스 및 Magento Open Source 버전 2.4.0의 경우 Elasticsearch 6.x 또는 7.x가 필수 구성 요소이며 MySQL 검색 엔진이 제거됩니다. 클라우드 인프라의 Adobe Commerce에서는 Elasticsearch이 이미 필요합니다.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거됩니다.

Adobe Commerce 온프레미스, Adobe Commerce 온클라우드 인프라 및 Magento Open Source 2.4.0이 향후 몇 개월 내에 출시될 예정입니다. Adobe Commerce 온-프레미스 및 Magento Open Source 버전 2.4.0의 경우 Elasticsearch 6.x 또는 7.x가 필수 구성 요소이며 MySQL 검색 엔진이 제거됩니다. 클라우드 인프라의 Adobe Commerce에서는 Elasticsearch이 이미 필요합니다.

>[!WARNING]
>
>업그레이드를 시도하기 전에 Elasticsearch 6/7을 설치/구성하지 않으면 Adobe Commerce에 심각한 문제가 발생할 수 있습니다. 클라우드 인프라에서 Adobe Commerce의 서비스 업그레이드는 48시간 동안 인프라 팀에 통보하지 않으면 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 사항이 프로덕션에 적용되기 48시간 전에 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 필요한 서비스 업그레이드에 대해 자세히 설명하고 업그레이드 프로세스를 시작할 시간을 지정하십시오.

MySQL 검색 엔진을 제거하는 이유는 Elasticsearch이 카탈로그 성능 최적화와 함께 뛰어난 검색 기능을 제공하기 때문입니다.

## 영향을 받는 제품 및 버전:

* Adobe Commerce 온-프레미스 v2.4.0
* Magento Open Source v2.4.0

## 업그레이드:

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>검색 엔진</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>작업</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">Elasticsearch을 설치해야 합니다. 개발자 설명서에서 <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search">Elasticsearch 설치 및 구성</a>을 참조하십시오.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch(나열된 버전 없음)</td>
<td style="width: 478.2px;">Elasticsearch 2를 사용 중이며 Elasticsearch 7(기본 설정) 또는 6으로 업데이트해야 합니다. 자세한 내용은 개발자 설명서에서 <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Elasticsearch 업그레이드</a> 및 <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine">Elasticsearch을 사용하도록 Commerce 구성</a>을 참조하십시오.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5는 <a href="https://www.elastic.co/support/eol">수명 종료</a>에 도달하여 Adobe Commerce 2.4.0에서 더 이상 사용되지 않습니다. Elasticsearch 7(기본 설정) 또는 6으로 업데이트합니다.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 또는 7</td>
<td style="width: 478.2px;">Adobe Commerce 2.4.0으로 업그레이드하기 전에 추가 단계를 수행할 필요가 없습니다.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">타사 확장</td>
<td style="width: 478.2px;">Elasticsearch을 설치할 필요는 없습니다. Adobe Commerce은 확장이 Adobe Commerce 2.4.0과 완전히 호환되는지 여부를 확인하기 위해 검색 엔진 공급업체에 문의할 것을 권장합니다.</td>
</tr>
</tbody>
</table>

## 설치:

Adobe Commerce 온-프레미스 및 Magento Open Source 2.4.0이 릴리스되면 Elasticsearch은 필수 구성 요소이므로 버전 2.4.0을 설치하기 전에 Elasticsearch 호스트를 설정하고 구성해야 합니다. 개발자 설명서에서 [Elasticsearch 설치 및 구성](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)을 참조하세요.

기본적으로 Adobe Commerce 검색은 Elasticsearch 7을 검색 엔진으로 사용하고 localhost:9200에서 서버에 연결을 시도합니다. Elasticsearch 6.x도 지원됩니다. 구성이 기본값과 일치하지 않으면 데이터베이스 연결이 구성된 것과 거의 동일한 방식으로 `setup:install`에 전달된 인수를 사용하여 이러한 설정을 구성할 수 있습니다.

For example, `setup:install --elasticsearch-host=es.mystore.com`

설치하는 동안 Elasticsearch 연결이 확인되며 Adobe Commerce에서 Elasticsearch 호스트에 연결할 수 없는 경우 설치에 실패합니다. 이 경우 Elasticsearch이 실행 중인지, 그리고 올바른 연결 매개 변수를 제공했는지 확인하십시오.
