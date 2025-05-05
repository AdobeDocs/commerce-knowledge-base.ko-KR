---
title: 오류  [!DNL opensearch] 검색 엔진이 없습니다.  [!DNL livesearch] (으)로 돌아갑니다.
description: 이 문서에서는 '오류- [!DNL opensearch] 검색 엔진이 존재하지 않는' 오류가 표시되는 문제에 대한 해결 방법을 제공합니다. 클라우드 인프라의 Adobe Commerce에서  [!DNL livesearch].&grave;으로 폴백합니다.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# 오류 [!DNL opensearch] 검색 엔진이 없습니다. [!DNL livesearch] (으)로 돌아갑니다.

이 문서에서는 오류: *오류: [!DNL opensearch] 검색 엔진이 없는 문제에 대한 해결 방법을 제공합니다. [!DNL livesearch] (으)로 돌아갑니다.[!DNL Live Search]이(가) 사용되는 클라우드 인프라의 Adobe Commerce에 있는*.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전
* [!DNL Live Search]이(가) 설치되어 사용 중입니다.

## 문제

다음 메시지가 로그에 표시됩니다([!DNL New Relic]에서 확인 가능).
*오류: [!DNL opensearch] 검색 엔진이 없습니다. [!DNL livesearch].*(으)로 폴백

## 솔루션

1. `.magento.env.yaml` 파일을 수정합니다.
1. 다음 줄을 찾습니다.

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. 이러한 줄이 없으면 `.magento.env.yaml` 파일에 추가하십시오.
1. 이 줄이 있으면 **엔진을 *[!DNL opensearch]*&#x200B;에서 *[!DNL livesearch]*(으)로 수정**&#x200B;합니다.
1. 변경 사항을 커밋한 다음 재배포합니다.

## 관련 읽기

* Live Search 가이드의 [설치 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)
