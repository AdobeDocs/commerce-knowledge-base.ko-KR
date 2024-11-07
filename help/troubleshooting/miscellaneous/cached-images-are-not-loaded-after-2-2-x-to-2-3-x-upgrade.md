---
title: 캐시된 이미지는 2.2.X에서 2.3.X로 업그레이드한 후 로드되지 않음
description: 이 문서에서는 클라우드 인프라 2.2.X의 Adobe Commerce에서 2.3.X로 업그레이드한 후 캐시된 이미지가 표시되지 않는 문제에 대한 해결 방법을 제공합니다.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# 캐시된 이미지는 2.2.X에서 2.3.X로 업그레이드한 후 로드되지 않음

이 문서에서는 클라우드 인프라 2.2.X의 Adobe Commerce에서 2.3.X로 업그레이드한 후 캐시된 이미지가 표시되지 않는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 버전 및 버전:

* Adobe Commerce on cloud infrastructure Pro 플랜 아키텍처 2.2.X, 2.3.X

## 문제

Adobe Commerce이 2.2.X에서 2.3.X로 업그레이드된 후 캐시된 제품 이미지를 사용할 수 없으며 대신 404 페이지가 표시됩니다.

`.magento.app.yaml`에 잘못된 Nginx 구성 집합이 있기 때문에 문제가 발생합니다. `passthru: /get.php` 대신 `"/media"` 위치에 `index.php`(또는 없음)을(를) 사용합니다.

## 솔루션

1. `"/media"` 위치에서 `.magento.app.yaml` 구성 파일을 확인하십시오. 올바른 구성은 다음과 같습니다.

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. `passthru`이(가) `"/get.php"`(으)로 설정되어 있지 않고 `expires`이(가) 설정되어 있지 않으면 다음 단계를 수행하십시오.
1. 구성 파일을 수정합니다.
   * 스타터 플랜: 파일을 직접 수정하고 변경 사항을 푸시합니다.
   * Pro 플랜:
   * 통합: 파일을 직접 수정하고 변경 사항을 푸시합니다.
   * 스테이징 및 프로덕션: 파일을 직접 수정하고 변경 내용을 푸시한 다음 [Adobe Commerce 지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 만들어 적용합니다.

1. <https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>에 설명된 대로 Commerce 관리자에서 Fastly 이미지 최적화를 활성화합니다(Fastly는 이전에 구성해야 함).

구성이 올바르지만 문제가 계속 발생하면 조사를 계속하거나 [Adobe Commerce 지원](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)에 문의하십시오.
