---
title: Google Analytics은 배포 후 비활성화됩니다.
description: 이 항목에서는 배포 중에 Google Analytics에 발생할 수 있는 일반적인 문제에 대한 해결 방법에 대해 설명합니다.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Google Analytics은 배포 후 비활성화됩니다.

이 항목에서는 배포 중에 Google Analytics에 발생할 수 있는 일반적인 문제에 대한 해결 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

환경 간에 코드를 배포할 때 빌드 및 배포 스크립트는 `master/production/staging` 분기가 배포되어 Google Analytics이 활성화되었는지 확인합니다. 마스터 의 개발(또는 하위) 분기를 개발자 환경(통합)에 배포할 때 배포 스크립트는 Google Analytics을 비활성화합니다.

## 원인

개발자 데이터 및 상호 작용이 Google Analytics으로 전송되거나 추적되지 않도록 하기 위한 기능입니다.

## 솔루션

Google Analytics을 항상 활성화하려면 개발자 설명서의 [변수 배포](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics)에 설명된 대로 배포 변수 `ENABLE_GOOGLE_ANALYTICS = true`을(를) 설정하십시오.

>[!NOTE]
>
>이 문서에는 일부 사람들이 인종차별주의자, 성차별주의자 또는 억압적이라고 생각할 수 있고 독자로 하여금 상처받거나, 트라우마를 받거나, 환영받지 못하게 만들 수 있는 업계 표준 소프트웨어 용어가 여전히 포함되어 있을 수 있다는 것을 알고 있습니다. Adobe이 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하고 있습니다.
