---
title: 데이터 및 파일 동기화 프로덕션을 스테이징에 또는 스테이징을 통합에
description: 이 문서에서는 클라우드 인프라에서 프로덕션 환경을 Adobe Commerce 스테이징으로 동기화하는 방법에 대해 설명합니다. 이는 불가능합니다.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 데이터 및 파일 동기화 프로덕션을 스테이징에 또는 스테이징을 통합에

이 문서에서는 프로덕션 환경을 클라우드 인프라의 Adobe Commerce 스테이징으로 동기화하는 방법에 대해 설명합니다. 사용자 인터페이스 또는 Magento 클라우드 CLI를 통해서는 안 됩니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.3.x, 2.4.x

## 한 환경에서 다른 환경으로 데이터를 동기화하려면

데이터를 동기화하려면 소스 환경에서 데이터베이스를 수동으로 덤프해야 합니다. 데이터를 다른 환경으로 전송하려면 소스 덤프를 타겟 환경으로 업로드한 다음 가져와야 합니다. 자세한 내용은 개발자 설명서에서 [Adobe Commerce 코드를 Cloud 프로젝트로 가져오기 > Adobe Commerce 데이터베이스 가져오기](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)를 참조하십시오.

Adobe Commerce on cloud infrastructure Pro 계획 아키텍처의 경우 스테이징 및 프로덕션에서 통합 마스터 분기로 동기화할 수도 있습니다. 이 동기화는 데이터를 가져오지 않고 코드만 가져오고 푸시합니다. 데이터를 동기화하려면 데이터베이스 데이터를 덤프하고 다른 환경의 데이터베이스에 푸시해야 합니다.

>[!WARNING]
>
>Pro 스테이징 및 프로덕션 클러스터에서는 데이터베이스를 동기화할 수 없습니다.

## 한 환경에서 다른 환경으로 파일을 동기화하려면

한 환경에서 다른 환경으로 파일을 동기화하려면 `rsync` 명령을 사용하십시오. 자세한 내용은 개발자 설명서에서 [코드 배포 및 정적 파일 및 데이터 마이그레이션 > rsync를 사용하여 파일 마이그레이션](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production#migrate-files-using-rsync)을 참조하십시오.

>[!NOTE]
>
>통합에서 스테이징으로 코드를 동기화하려면 통합 분기에서 동기화해야 합니다. 단계는 개발자 설명서에서 [환경의 상위 항목에서 동기화](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment)를 참조하십시오.
