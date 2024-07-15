---
title: 클라우드 인프라에서 Adobe Commerce의 배포 중단 시간 감소
description: 유지 관리 다운타임을 획기적으로 줄이고 환경 전반에 걸쳐 스토어를 효율적으로 구성할 수 있도록 Adobe Commerce on cloud infrastructure는 **구성 관리** 기능을 제공합니다. 클라우드 인프라 2.2.x 이상 구현의 Adobe Commerce에서 이 기능은 파이프라인 배포 개념과 옵션을 간소화된 단계로 지원합니다.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 클라우드 인프라에서 Adobe Commerce의 배포 중단 시간 감소

유지 관리 가동 중단을 크게 줄이고 환경 전반에 걸쳐 스토어를 효율적으로 구성할 수 있도록 Adobe Commerce on cloud infrastructure는 **구성 관리** 기능을 제공합니다. 클라우드 인프라 2.2.x 이상 구현의 Adobe Commerce에서 이 기능은 파이프라인 배포 개념과 옵션을 간소화된 단계로 지원합니다.

## 개요

웹 스토어 배포의 고통스럽고 시간이 많이 소요되는 문제는 다음과 같습니다.

* **모든 환경에서 동일한 구성을 적용합니다.** 일반적으로 구성을 수동으로 입력하거나 복잡한 데이터베이스 업데이트를 통해 입력해야 합니다. 구성 관리를 사용하면 데이터베이스에서 구성을 단일 파일로 내보내 나중에 로컬 개발 환경에서 코드를 사용하여 통합, 스테이징 및 프로덕션으로 푸시할 수 있습니다.

* **정적 콘텐츠를 배포할 때 사이트 가동 중지 시간.** 일반적으로 정적 콘텐츠는 [배포 단계](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) 중에 배포됩니다. 이 작업은 최대 30분 이상 소요될 수 있으므로 비즈니스에 적합하지 않습니다. 구성 관리는 정적 콘텐츠 배포를 [빌드 단계](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase)(으)로 이동하며, 가동 중지 시간이 필요하지 않습니다.

## 기술 버전

* 구성 관리를 위한 클라우드 인프라 **2.1.4** 이상 버전의 Adobe Commerce
* 구성 관리/파이프라인 배포용 클라우드 인프라 **2.2** 이상 버전의 Adobe Commerce

## 구성 관리란?

간단히 말해 구성 관리(파이프라인 배포라고도 함) 프로세스는 Adobe Commerce on cloud infrastructure 구현(데이터베이스)의 모든 구성 설정을 단일 PHP 파일로 추출합니다. 그런 다음 파일을 Git 커밋에 추가하고 모든 환경에 푸시합니다.

이렇게 하면 다음과 같은 이점이 있습니다.

* **모든 환경에서 일관된 설정:** 구성 파일로 내보내는 모든 설정은 잠겨지고(Commerce 관리자의 해당 필드는 읽기 전용임), 모든 환경에서 파일을 푸시할 때 일관된 구성을 보장합니다.
* **가동 중지 시간 감소:** 정적 파일 배포가 [배포 단계](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase)(사이트가 유지 관리 모드에 있어야 함)에서 [빌드 단계](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase)(사이트가 유지 관리 모드에 있지 않고 오류 또는 문제가 발생할 경우 중단되지 않음)로 이동합니다.
* **보호된 중요 데이터:** 클라우드 인프라 2.2 이상에서 Adobe Commerce을 사용하면 이 프로세스는 중요 데이터(예: 결제 게이트웨이 자격 증명)도 `env.php` 파일로 내보냅니다. 이 파일은 Git 분기와 함께 푸시되지 않고 작성된 환경에만 저장해야 합니다.

배포에 구성 관리 접근 방식을 적용하는 것이 좋습니다.

## 개발자 설명서의 구성 관리

* *Adobe Commerce on cloud infrastructure 안내서*&#x200B;의 **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 및 [예](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)에 대한 [구성 관리
* *Adobe Commerce on cloud infrastructure 안내서*&#x200B;의 **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 및 [예](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)에 대한 [구성 관리
* *클라우드 인프라에서 Adobe Commerce 업그레이드* 항목의 [2.0.X 또는 2.1.X에서 업그레이드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) 섹션
* *Adobe Commerce on cloud infrastructure 구성 안내서의 [파이프라인 배포](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html)* - Adobe Commerce on cloud infrastructure의 경우 이 안내서의 지침을 따르지 않아도 됩니다. 그 내용은 참고용이다. Dell은 이미 클라우드 인프라에서 Adobe Commerce을 사용하여 빌드 서버, 통합 환경 등을 제공하고 있습니다.
