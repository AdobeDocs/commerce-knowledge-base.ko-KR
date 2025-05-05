---
title: robots.txt가 업데이트되지 않거나 기본 설정이 표시됨
description: 이 문서에서는 예를 들어 [Adobe Commerce robots.txt 우수 사례](https://support.magento.com/hc/en-us/articles/360048754931)에 따라 'robots.txt'를 올바르게 구성했지만 'robots.txt'가 업데이트되지 않거나 기본 설정이 표시되는 경우를 위한 솔루션을 제공합니다.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt가 업데이트되지 않거나 기본 설정이 표시됨

이 문서에서는 [Adobe Commerce robots.txt에 대한 모범 사례](https://support.magento.com/hc/en-us/articles/360048754931)에 따라 `robots.txt`을(를) 올바르게 구성했지만 `robots.txt`이(가) 업데이트되지 않거나 기본 설정을 표시하는 경우에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.3.x, 2.4.x

## 문제

기본 `robots.txt` 설정을 변경할 수 없습니다.

<u>재현 단계:</u>

1. 관리 패널에 액세스합니다.
1. **콘텐츠** > 디자인 > **구성** > **텍스트 &quot;hello&quot;와 같은`robots.txt`** 파일의 사용자 지정 지침 편집&rbrace;에 콘텐츠를 추가하고 변경 내용을 저장합니다.
1. `robots.txt` URL을 방문하십시오.

<u>예상 결과:</u>
`robots.txt`에 저장된 텍스트가 있습니다.

<u>실제 결과:</u>

`robots.txt` 파일이 변경되지 않습니다.

## 원인

검색 엔진에 의한 색인화가 해제되었습니다.

## 솔루션

검색 엔진별 색인화를 활성화합니다. 개발자 설명서에서 [검색 엔진별 색인화 구성](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine)을 참조하십시오.

## 관련 읽기

* 개발자 설명서에서 [사이트 맵 및 검색 엔진 로봇을 추가](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)합니다.
