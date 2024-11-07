---
title: 캐시 준비 및 Adobe Commerce에서 사이트를 사용할 수 없음
description: 이 문서에서는 페이지 캐시가 준비 중이고 중단된 배포 또는 사이트 다운이 있는 경우에 대한 솔루션을 제공합니다.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 캐시 준비 및 Adobe Commerce에서 사이트를 사용할 수 없음

이 문서에서는 페이지 캐시가 준비 중이고 중단된 배포 또는 사이트 다운이 있는 경우에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 문제

사후 배포 단계가 끝날 때 캐시 준비 스크립트는 4-cpu 인스턴스와 같은 특정 인스턴스가 처리할 수 없을 만큼 높은 비율로 요청을 보냅니다. 그들의 통찰력은 노동자의 수를 소모한다.

<u>재현 단계</u>:

캐시 준비 작업을 시작합니다.

<u>예상 결과</u>:

페이지 또는 전체 사이트가 로드됩니다.

<u>실제 결과</u>:

사이트를 사용할 수 없거나 응답 시간이 너무 깁니다.

## 솔루션

캐시 준비 중 동시 연결 수를 제한합니다. 이를 위해서는 `WARM_UP_CONCURRENCY` 사후 배포 변수를 추가하여 캐시 준비 스크립트에서 동시에 보낼 수 있는 준비 요청의 수를 지정해야 합니다. 이 옵션을 설정하면 Adobe Commerce 클라우드 인프라의 로드를 관리하는 데 도움이 될 수 있습니다. 개발자 설명서에서 [배포 후 변수 > WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency)을(를) 참조하십시오.

## 관련 읽기

사용 안내서의 [전체 페이지 캐시](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching)
