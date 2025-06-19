---
title: 처리량이 많은 AJAX 요청으로 인해 성능이 저하됨
description: 이 문서에서는 처리량이 많은 일부 요청으로 인해 상당한 서버 로드 및 트래픽이 발생하여 Adobe Commerce 온프레미스 또는 Adobe Commerce 기반 구조 사이트의 성능 문제에 대한 솔루션을 제공합니다.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 처리량이 많은 AJAX 요청으로 인해 성능이 저하됨

이 문서에서는 처리량이 많은 일부 요청으로 인해 상당한 서버 로드 및 트래픽이 발생하여 Adobe Commerce 온프레미스 또는 Adobe Commerce 기반 구조 사이트의 성능 문제에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce 온-프레미스 2.2.x, 2.3.x

>[!NOTE]
>
>Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 버전 2.3.4에서 문제가 해결되었습니다.

### 문제

중요한 AJAX 요청과 같이 처리량이 많은 요청으로 인해 사이트의 성능이 저하됩니다.

### 원인

처리량이 많은 AJAX 요청에는 고객의 개인 컨텐츠와 관련된 요청이 포함됩니다.

### 솔루션

세 가지 솔루션이 있습니다.

* [버전 2.3.4](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)&#x200B;(으)로 업그레이드
* 더 가벼운 요청(캐시 요청 또는 고객의 개인 컨텐츠로 이동)을 확인하십시오.
* 요청 수를 줄입니다.

<u>더 가벼운 요청(요청을 캐시하거나 고객의 개인 콘텐츠로 이동)을 확인합니다</u>

각 페이지에서 트리거되는 서드파티 AJAX 요청이 있는 경우 이러한 요청을 캐시하거나 고객의 개인 콘텐츠로 이동하려고 합니다. 판매자는 사용자 지정 AJAX 요청이 GET HTTP 메서드를 사용하여 호출되는지 확인하여 이 작업을 수행할 수 있습니다. Fastly를 통해 이러한 요청을 취소할 수 있습니다. 캐시해서는 안 되는 사용자 지정 AJAX 요청이 있는 경우 개인 콘텐츠 기능에 따라 리팩터링해야 합니다. 단계는 개발자 설명서에서 [비공개 콘텐츠](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)를 참조하십시오.

<u>요청 수 감소</u>

* `customer/section/load`개의 요청 수를 늘릴 수 있으므로 영구 장바구니를 비활성화하십시오. 개발자 설명서에서 [지속적인 장바구니 경로](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/paths/config-reference-general)의 단계에 따라 지속적인 장바구니가 활성화되어 있는지 확인하십시오.
* `sections.xml`에서 콘텐츠를 다시 로드하거나 무효화해야 하는 경우 개발자 설명서에서 [개인 콘텐츠: 개인 콘텐츠 무효화](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)의 단계를 따르십시오. 사용자 지정에서 직접 `customerData.reload()` 메서드를 사용하고 있지 않은지 확인하십시오.
* 동일한 페이지에서 다른 POST AJAX 요청을 확인합니다. Google Chrome 브라우저에서 Google Chrome 개발자 도구를 엽니다. **네트워크** 탭을 클릭한 다음 **XHR** 탭을 클릭하면 특정 페이지의 모든 AJAX 요청 목록이 표시됩니다. 그런 다음 각 요청을 클릭하고 필드의 요청 방법 이 GET 요청이어야 합니다. 참고: Google Chrome이 예로 사용되며 다른 브라우저에서도 이 작업을 수행할 수 있습니다.
* 특정 AJAX 요청인 Google 태그 관리자(GTM) 기능을 확인합니다. 사용자는 이 AJAX을 제거하고 개인 기능으로 사용자 지정을 리팩터링하여 서버에 대한 총 요청 수를 줄일 수 있습니다.
* Adobe Commerce 배너가 활성화되어 있지만 사용되지 않는지 확인합니다. 사이트 성능을 향상시키려면 [Adobe Commerce 배너 출력을 사용하지 않도록 설정](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909)해야 할 수 있습니다.

### 관련 읽기

개인 고객 콘텐츠에 대한 자세한 내용은 개발자 설명서에서 [개인 콘텐츠](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)를 검토하세요.
