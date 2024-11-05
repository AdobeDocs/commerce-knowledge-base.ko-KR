---
title: '''app/etc/env.php''에서 검색 엔진을 변경할 수 없음'
description: 이 문서에서는 Commerce 관리자의 검색 엔진을 변경하려고 하지만 필드가 잠겨 있는 문제에 대한 해결 방법을 제공합니다.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: bc800397a3c0c3a86eb717db60e445e13b299688
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# `app/etc/env.php`에서 검색 엔진을 변경할 수 없습니다.

이 문서에서는 `app/etc/env.php` 파일에서 검색 엔진 구성을 제거하려고 하지만 다시 배포한 후 구성이 이전 설정으로 되돌아가거나 기본적으로 [!DNL OpenSearch](으)로 변경되는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

Commerce 관리에서 검색 엔진을 변경하려고 하지만 필드가 잠겨 있습니다.

## 원인

검색 엔진 구성이 `app/etc/env.php` 파일에서 잠겨 있거나 검색 엔진이 `.magento.env.yaml` 파일에 명시적으로 정의되어 있습니다.

## 솔루션

1. 배포 단계에서 `.magento.env.yaml` 파일을 확인하고 `SEARCH_CONFIGURATION` 변수가 구성되었는지 확인하십시오. 예:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. `SEARCH_CONFIGURATION` 변수가 있습니까? 검색 엔진 구성이 없으면 기본적으로 [!DNL OpenSearch](으)로 잠깁니다. 구성을 변경하려면 검색 엔진에 적절한 값이 있는 `.magento.env.yaml` 파일에 변수를 추가해야 합니다. `SEARCH_CONFIGURATION` 변수가 있고 엔진을 수정하려면 `.magento.env.yaml`에서 엔진의 기존 값을 바꾸십시오. 가능한/알려진 값: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] 및 [!DNL amasty_elastic_opensearch].
1. 인스턴스를 재배포합니다.
1. 관리자의 검색 엔진 필드는 잠겨 있지만 지정한 값으로 업데이트되어야 합니다.

## 관련 읽기

* Cloud Infrastructure Guide의 Commerce Commerce Admin에서 [잠긴(회색으로 표시됨) 필드](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md).
