---
title: 고급 검색에 가장 관련성이 높은 결과가 표시되지 않음
description: 이 문서에서는 고급 검색이 가장 관련성이 높은 결과를 먼저 표시하지 않는 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# 고급 검색에 가장 관련성이 높은 결과가 표시되지 않음

이 문서에서는 고급 검색이 가장 관련성이 높은 결과를 먼저 표시하지 않는 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.

## 영향을 받는 버전 {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce(모든 배포 옵션) 2.x.x
* Magento Open Source 2.x.x

## 문제 {#Advancedsearchnotshowingmostrelevantresults-Description}

고급 검색 기능은 빠른 검색처럼 가장 관련성이 높은 결과를 먼저 반환하지 않습니다. 선택한 검색 엔진 유형에 따라 문제가 달라지지 않습니다.

<u>재현 단계:</u>

1. 상점 앞에서 빠른 검색어로 이동하여 &quot;Fitted Jacket&quot;을 검색하십시오.
1. &quot;Orion Two-Tone Fitted Jacket&quot;이 첫 번째 결과입니다.
1. 고급 검색으로 이동한 다음 이름 필드에서 &quot;Fitted Jacket&quot;을 검색합니다.

<u>예상 결과:</u>

고급 검색을 사용할 때 가장 연관성이 높은 결과로는 &#39;오리온 투톤 핏티드 재킷&#39;이 첫 번째 결과다.

<u>실제 결과:</u>

가장 연관성이 높지만 &#39;오리온 투톤 핏티드 재킷&#39;은 첫 번째 결과는 아니다.

## 솔루션 {#Advancedsearchnotshowingmostrelevantresults-Solution}

이 문제를 해결하려면 이 문서에 첨부된 패치를 적용합니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-7256\_EE\_2.1.7\_v1.composer.patch 다운로드](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

이 패치는 고급 검색 결과에 대한 관련성을 기준으로 정렬하는 구현을 기본 정렬 필드로 추가합니다.

이 패치는 영향을 받는 모든 버전 및 버전과 호환됩니다.

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
