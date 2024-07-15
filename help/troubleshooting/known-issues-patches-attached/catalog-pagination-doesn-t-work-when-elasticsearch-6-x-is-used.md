---
title: 카탈로그 페이지 매김이 Elasticsearch 6.x에서 작동하지 않음
description: 이 문서에서는 Elasticsearch 6.x에서 카탈로그 페이지 매김이 작동하지 않는 Adobe Commerce 문제에 대한 패치를 제공합니다.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 카탈로그 페이지 매김이 Elasticsearch 6.x에서 작동하지 않음

이 문서에서는 Elasticsearch 6.x에서 카탈로그 페이지 매김이 작동하지 않는 Adobe Commerce 문제에 대한 패치를 제공합니다.

아래 패치는 Elasticsearch 6.x가 카탈로그 검색 엔진으로 사용되는 배포에서 Adobe Commerce 2.3.3 사용자가 겪는 문제를 해결합니다. 사용자가 검색 결과의 첫 페이지를 지나서 탐색하려고 하면 오류 메시지가 표시됩니다.

이 패치가 설치되면 사용자는 모든 검색 결과를 페이징할 수 있습니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.3.3
* Adobe Commerce 온-프레미스 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## 문제

페이지를 전환하면 검색 결과 페이지 매김이 작동하지 않는 Magento Open Source, Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure에서 문제가 발견되었습니다.

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. 카탈로그 검색 엔진으로 Elasticseach 6을 활성화합니다.
1. 관리자에 설정된 1페이지 제한을 초과하는 제품 수를 범주에 추가합니다. **참고**: 12는 Adobe Commerce 2.3.3에서 페이지당 표시되는 기본 제품 수입니다.
1. 상점 첫 화면에서 카테고리(검색 결과 또는 카테고리 페이지)를 열고 2페이지로 이동합니다.

<u>예상 결과</u>:

제품은 두 번째 페이지에 표시되어야 합니다.

<u>실제 결과</u>:

**&quot;***선택 항목과 일치하는 제품을 찾을 수 없습니다.***&quot;** 메시지가 두 번째 페이지에 표시됩니다.

## 솔루션

이 문제를 해결하려면 이 문서에 첨부된 패치를 적용하십시오. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[Elasticsearch 6.x 패치의 카탈로그 페이지 매김 문제](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - 패치가 영향을 받는 모든 버전 및 버전과 호환됩니다.

>[!WARNING]
>
>Adobe은 증상이 없더라도 최대한 빨리 패치를 붙이는 것을 적극 권장합니다.

## 패치 적용 방법

지침은 [Adobe Commerce에서 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
