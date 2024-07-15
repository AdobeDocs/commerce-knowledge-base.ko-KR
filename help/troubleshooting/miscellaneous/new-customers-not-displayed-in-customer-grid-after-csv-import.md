---
title: CSV 가져오기 후 새 고객이 고객 그리드에 표시되지 않음
description: 이 문서에서는 ".csv" 파일에서 가져온 후 **Customers** &gt; **All customers** 아래에 새 고객이 표시되지 않을 때 발생하는 문제를 해결합니다. 해결 방법은 'customer_grid' 인덱서를 "저장 시 업데이트" 모드로 설정하고 고객 그리드를 수동으로 다시 인덱싱하는 것입니다.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# CSV 가져오기 후 새 고객이 고객 그리드에 표시되지 않음

이 문서에서는 `.csv` 파일에서 가져온 후 **고객** > **모든 고객**&#x200B;에서 새 고객을 볼 수 없을 때 발생하는 문제를 해결합니다. 해결 방법은 `customer_grid` 인덱서를 &quot;저장 시 업데이트&quot; 모드로 설정하고 고객 그리드를 수동으로 다시 인덱싱하는 것입니다.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스 2.2.0 이상
* cloud infrastructure 2.2.0 이상 버전의 Adobe Commerce

## 문제

기본 Adobe Commerce 가져오기 기능을 사용하여 `.csv` 파일에서 새 고객을 가져온 후에는 `customer_grid` 인덱서를 수동으로 다시 인덱싱할 때까지 관리자의 **고객** > **모든 고객**&#x200B;에서 새 고객 레코드를 볼 수 없습니다.

## 원인

성능 문제로 인해 Adobe Commerce 2.2.0 이상의 &quot;일정에 따라 업데이트&quot; 인덱싱 모드는 `customer_grid` 인덱서를 지원하지 않습니다.

## 솔루션

&quot;저장 시 업데이트&quot; 모드를 사용하여 다시 인덱싱할 `customer_grid` 인덱서를 구성하십시오. 이렇게 하려면 다음 단계를 수행합니다.

1. Commerce 관리자에 로그인합니다.
1. **시스템** > **도구** > **색인 관리**&#x200B;를 클릭합니다.
1. Customer Grid Indexer 옆에 있는 확인란을 선택합니다.
1. **작업** 드롭다운 목록에서 *저장 시 업데이트*&#x200B;를 선택합니다.
1. **제출**&#x200B;을 클릭합니다.

또한 색인이 최신 상태이고 cron을 사용하여 작업할 수 있도록 색인화 모드를 구성한 후 `customer_grid` 색인을 수동으로 다시 색인화하는 것이 좋습니다. 수동으로 다시 색인화하려면 다음 명령을 사용합니다.

`bin/magento indexer:reindex customer_grid`

## 추가 정보

개발자 설명서 관련 항목 링크:

* [인덱싱 개요](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [인덱서 관리](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
