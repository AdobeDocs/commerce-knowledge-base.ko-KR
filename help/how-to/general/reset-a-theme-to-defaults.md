---
title: 테마를 기본값으로 재설정
description: 테마를 맞춤화하고 스토어를 개발할 때 발생할 수 있는 문제에 따라 Commerce 관리자를 통해 액세스할 수 없습니다. 관리자에 액세스하지 않고 테마 기본값을 지우고 재설정할 수 있습니다. 테마를 지우면 기본 Luma 테마가 적용됩니다.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# 테마를 기본값으로 재설정

테마를 맞춤화하고 스토어를 개발할 때 발생할 수 있는 문제에 따라 Commerce 관리자를 통해 액세스할 수 없습니다. 관리자에 액세스하지 않고 테마 기본값을 지우고 재설정할 수 있습니다. 테마를 지우면 기본 Luma 테마가 적용됩니다.

Adobe Commerce(모든 배포) 및 Magento Open Source 구성 요소(모듈, 테마 및 언어 패키지)를 개발하는 동안 빠르게 변화하는 환경에서 특정 디렉터리 및 캐시를 정기적으로 지워야 합니다. 그렇지 않으면 코드가 예외와 함께 실행되고 제대로 작동하지 않습니다. 자세한 내용은 개발자 설명서에서 [개발 중 디렉터리 지우기](https://developer.adobe.com/commerce/php/development/components/clear-directories/)를 참조하십시오.

## 환경 및 기술

* Adobe Commerce 온-프레미스
* 클라우드 인프라의 Adobe Commerce
* Magento Open Source

## 전제 조건

* 데이터베이스 도구

## 단계

스토어 테마를 재설정해야 하지만 관리 패널에 액세스할 수 없는 경우, 다음을 수행하여 데이터베이스에서 재설정할 수 있습니다.

1. [phpMyAdmin](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)과 같은 데이터베이스 도구를 사용하거나 명령줄에서 DB에 수동으로 액세스하여 다음 SQL 쿼리를 실행합니다. `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. 다음 디렉터리를 지웁니다.
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

이렇게 하면 스토어 보기 수준에 테마 설정이 없으며 스토어 전면 페이지를 다시 로드할 때 기본 Luma 테마가 적용됩니다.

## 추가 정보

* 개발자 설명서에서 [개발 중 디렉터리 지우기](https://developer.adobe.com/commerce/php/development/components/clear-directories/)
