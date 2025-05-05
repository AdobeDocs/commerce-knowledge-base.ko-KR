---
title: 배포 후 표시되지 않는 이미지 저장
description: 이 문서에서는 배포 후 이미지가 올바르게 표시되지 않는 문제에 대한 해결 방법을 제공합니다.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# 배포 후 표시되지 않는 이미지 저장

이 문서에서는 배포 후 이미지가 올바르게 표시되지 않는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x

## 문제

이미지 크기 조정과 함께 상점 테마를 사용하는 경우 배포 시 이미지가 카탈로그 페이지에서 표시되지 않거나 사라집니다.

## 원인

이 문제는 캐시에서 이미지를 로드하기 때문에 발생할 수 있습니다.

## 솔루션

이 경우 Magento 명령을 사용하여 이미지 캐시를 재생성하고 이미지를 올바르게 표시할 수 있습니다.

이를 수행하려면 SSH 정보와 [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=ko)을 통해 사용할 수 있는 저장소 URL이 필요합니다.

1. 개발자 설명서의 [환경에 대한 SSH](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/secure-connections)에 설명된 대로 [데이터베이스 덤프](/help/how-to/general/create-database-dump-on-cloud.md)의 소스인 프로젝트에 대한 SSH입니다.
1. 다음을 실행하여 이미지 캐시를 재생성합니다.

   ```bash
   php bin/magento catalog:images:resize
   ```

1. 스토어 URL을 통해 카테고리 페이지를 테스트합니다.
