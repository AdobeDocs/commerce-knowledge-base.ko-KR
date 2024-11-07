---
title: Adobe Commerce 배너 출력을 비활성화하여 사이트 성능 향상
description: 이 문서에서는 낮은 사이트 성능에 대한 수정 사항을 제공합니다. 'Magento_배너' 모듈은 활성화되지만 사용되지 않으므로 사이트 성능이 저하될 수 있습니다. 모듈 출력을 비활성화하면 사이트 성능이 향상될 수 있습니다. 해결 절차에 대해서는 문서를 검토하십시오.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce 배너 출력을 비활성화하여 사이트 성능 향상

이 문서에서는 낮은 사이트 성능에 대한 수정 사항을 제공합니다. `Magento_Banner` 모듈을 사용하도록 설정했지만 사용하지 않아 사이트 성능이 저하될 수 있습니다. 모듈 출력을 비활성화하면 사이트 성능이 향상될 수 있습니다. 해결 절차에 대해서는 문서를 검토하십시오.

>[!NOTE]
>
>Adobe Commerce 배너 기능을 사용하는 경우 과도한 Ajax 요청으로 인한 성능 문제를 방지하는 방법에 대한 권장 사항은 지원 기술 자료의 [높은 처리량의 AJAX 요청이 성능 저하를 일으킴](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) 문서를 참조하십시오.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce v.2.x.x
* Adobe Commerce 온-프레미스 v.2.2.x 및 2.3.x

## 문제

`Magento_Banner` 모듈이 사용하도록 설정되어 있지만 사용되지 않습니다.

이 경우에 해당하는지 확인하려면:

클라우드 인프라 2.2.x의 Adobe Commerce:

1. Commerce 관리자에 로그인합니다.
1. **콘텐츠** > *요소* > **배너**&#x200B;로 이동합니다.
1. 이 페이지에 표시된 표가 비어 있으면 배너가 없습니다.

**콘텐츠** > *요소* 아래에 **배너** 옵션이 표시되지 않는 경우 그렇지 않으며 이 문서의 권장 사항을 적용할 수 없습니다.

클라우드 인프라 2.3.x의 Adobe Commerce(기능이 [v 2.3.x에서 이름이 변경됨](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block))의 경우:

1. Commerce 관리자에 로그인합니다.
1. **콘텐츠** > *요소 >* **동적 블록**&#x200B;으로 이동합니다.
1. 이 페이지에 표시된 그리드가 비어 있으면 동적 블록(배너)이 없습니다.

**콘텐츠** > *요소* 아래에 **동적 블록** 옵션이 표시되지 않는 경우 그렇지 않으며 이 문서의 권장 사항을 적용할 수 없습니다.

## 원인

`Magento_Banner` 모듈이 활성화되면 Adobe Commerce은 배너 정보를 가져오기 위해 상점 전선에서 서버로 Ajax 요청을 보냅니다. 이러한 Ajax 요청은 특히 높은 로드(대량 및 높은 트래픽) 조건에서 성능에 영향을 줍니다. 이 기능을 사용하지 않는 경우에는 모듈 출력을 비활성화하는 것이 좋습니다. 종속성 문제로 인해 모듈을 비활성화하지 않는 것이 좋습니다.

## 솔루션

>[!WARNING]
>
>프로덕션에 적용하기 전에 먼저 [스테이징/통합 환경](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)에서 변경 사항을 테스트하는 것이 좋습니다. 또한 조작하기 전에 최근 백업을 수행하는 것이 좋습니다.

1. 개발자 설명서의 [모듈 출력 사용 안 함](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output)에 설명된 대로 `Magento_Banner` 모듈 출력을 사용하지 않도록 설정합니다. 모듈 이름은 `Magento_Banner`입니다.
1. 코드 배포. 클라우드 인프라의 Adobe Commerce의 경우 개발자 설명서의 [스토어 배포](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) 문서에 설명된 대로 배포하십시오.
