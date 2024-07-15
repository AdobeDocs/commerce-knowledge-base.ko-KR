---
title: 로그에 "무결성 제약 조건 위반"이 있는 저장소 전면 카탈로그 페이지에 503 오류 발생
description: 이 문서에서는 저장소 전면 카탈로그 페이지에 액세스할 수 없는 것과 관련된 클라우드 인프라 2.2.0의 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# 로그에 &quot;무결성 제약 조건 위반&quot;이 있는 저장소 전면 카탈로그 페이지에 503 오류 발생

>[!NOTE]
>
>이 문서에서는 해결 방법으로 패치를 제공하지만 이 문제는 Adobe Commerce on cloud infrastructure v2.3.3 릴리스에서 영구적으로 수정되었습니다. v2.3.3으로 업그레이드하는 것이 좋습니다. 개발자 설명서에서 [Adobe Commerce 버전 업그레이드](https://devdocs.magento.com/cloud/project/project-upgrade.html)의 단계를 따릅니다.

Adobe Commerce 이 문서에서는 로그: *무결성 제약 조건 위반: 1062 키 &#39;PRIMARY&#39;에 대한 항목 &#39;%entry%&#39;가 중복되었습니다. 쿼리: INSERT INTO \`search\_tmp\_%number%*.

## 문제

예기치 않게 스토어 전면 카탈로그 페이지에 액세스할 수 없습니다. 오류 로그에 다음과 유사한 오류 설명이 있습니다. *무결성 제약 조건 위반: 1062 키 &#39;PRIMARY&#39;에 대한 &#39;%entry%&#39; 항목이 중복되었습니다. 쿼리: INSERT INTO \&#39;search\_tmp\_%number%*.

검색과 관련된 문제로 색인 재지정 후 새 색인과 함께 오래된 색인이 존재하여 발생합니다.

## 솔루션

이 문제를 해결하려면 Elasticsearch 시 오래된 색인을 제거하고 패치를 적용하여 색인이 표시되지 않도록 해야 합니다.

모든 색인을 나열하려면 다음 명령을 사용합니다.

<pre>curl -X GET %elasticsearch_domain%:%elasticsearch_port%/_cat/indexes</pre>

오래된 색인을 제거하려면 데이터베이스에서 찾은 다음 다음 명령을 사용합니다.

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

예:

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## 패치

패치는 이 문서에 첨부되어 있습니다. 패치를 다운로드하려면 문서 끝까지 아래로 스크롤하여 필요한 파일 이름을 클릭하거나 다음 링크 중 하나를 클릭합니다.

[MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch 다운로드](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch 다운로드](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## 호환 가능한 Adobe Commerce 버전

패치는 다음 에디션 및 버전에 대해 작성되었습니다.

* 클라우드 인프라 2.2.0의 Adobe Commerce(`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* 클라우드 인프라 2.2.4(`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)의 Adobe Commerce

`MDVA-9590_EE_2.2.0_COMPOSER_v2` 패치는 다음 Adobe Commerce 버전 및 버전과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라 2.0.X, 2.1.X, 2.2.X 및 2.3.0 - 2.3.3의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.0.X, 2.1.X, 2.2.X 및 2.3.0 - 2.3.3

`MDVA-13203_EE_2.2.4_V1_COMPOSER` 패치는 다음 Adobe Commerce 버전 및 버전과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라 2.0.X, 2.1.X, 2.2.X 및 2.3.0 - 2.3.3의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.0.X, 2.1.X, 2.2.X 및 2.3.0 - 2.3.3

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 유용한 링크

* 지원 기술 자료에서 [클라우드 인프라 시작 계획 아키텍처의 Adobe Commerce에 대한 로그 파일 위치](/help/how-to/general/log-locations-directories-for-starter-plan.md)를 참조하십시오.
* 지원 기술 자료에서 [클라우드 인프라 Pro 계획 아키텍처의 Adobe Commerce에 대한 로그 파일 위치](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)를 참조하십시오.
* 개발자 설명서에서 [Adobe Commerce의 로그 파일 위치](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)를 참조하십시오.

## 첨부 파일
