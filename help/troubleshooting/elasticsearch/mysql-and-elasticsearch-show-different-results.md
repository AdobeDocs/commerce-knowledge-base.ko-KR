---
title: MySQL과 Elasticsearch에 다른 결과가 표시됨
description: 이 문서에서는 MySQL 및 Elasticsearch을 사용하여 동일한 검색 쿼리에 대해 서로 다른 검색 결과를 가져오는 것과 관련된 알려진 Adobe Commerce on cloud infrastructure 2.2.3 문제에 대한 패치를 제공합니다.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL과 Elasticsearch에 다른 결과가 표시됨

>[!WARNING]
>
> [MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거됩니다](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). 버전 2.4.0을 설치하기 전에 Elasticsearch 호스트를 설정하고 구성해야 합니다. 개발자 설명서에서 [Elasticsearch 설치 및 구성](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/search/overview-search)을 참조하세요.

이 문서에서는 MySQL 및 Elasticsearch을 사용하여 동일한 검색 쿼리에 대해 서로 다른 검색 결과를 가져오는 것과 관련된 알려진 Adobe Commerce on cloud infrastructure 2.2.3 문제에 대한 패치를 제공합니다.

## 문제:

필터 세트가 동일한 카탈로그 검색 결과는 사용 중인 검색 엔진, MySQL 또는 Elasticsearch에 따라 다릅니다.

<u>재현 단계</u>:

1. Elasticsearch 설치 및 구성
1. 상점 첫 화면에서 필터 중 하나를 선택합니다.
1. 일치하는 제품의 수를 기록합니다.
1. 기본 [MySQL 검색](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)을 구성하십시오.
1. 상점 첫 화면에서 필터 중 하나를 선택합니다.
1. 일치하는 제품의 수를 기록합니다.

<u>예상 결과</u>:
일치하는 제품의 수는 동일합니다.

<u>실제 결과</u>:
일치하는 제품의 수가 다릅니다.

## 패치

패치는 이 문서에 첨부되어 있습니다. 패치를 다운로드하려면 문서 끝까지 아래로 스크롤하여 필요한 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch 다운로드](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch 다운로드](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

패치는 다음에 대해 생성되었습니다.

* 클라우드 인프라 2.2.3(`MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` 파일)의 Adobe Commerce
* 클라우드 인프라 2.2.6(`MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` 파일)의 Adobe Commerce

`MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` 패치는 다음 Adobe Commerce 버전 및 버전과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라의 Adobe Commerce 2.2.4
* 클라우드 인프라의 Adobe Commerce 2.2.5
* Adobe Commerce 온-프레미스 2.2.3
* Adobe Commerce 온-프레미스 2.2.4
* Adobe Commerce 온-프레미스 2.2.5

`MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` 패치는 다음 Adobe Commerce 버전 및 버전과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce 온-프레미스 2.2.6

## 패치 적용 방법

자세한 내용은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
