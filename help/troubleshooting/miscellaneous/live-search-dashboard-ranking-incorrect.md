---
title: '[!DNL Live Search] 대시보드 및 검색 결과 순위가 올바르지 않음'
description: 이 문서에서는 [!DNL Live Search] 대시보드의 데이터가 올바르지 않거나 검색 결과의 순위가 예상과 다른 경우 문제 해결 정보를 제공합니다.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# [!DNL Live Search] 대시보드 및 검색 결과 순위가 올바르지 않음

[!DNL Live Search] 대시보드에 표시된 데이터가 올바르지 않거나 [검색 결과 순위](https://experienceleague.adobe.com/ko/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies)가 예상과 다른 경우 가능한 이유를 확인하려면 다음을 참조하십시오.

* `productView` 이벤트에 제품 컨텍스트의 `topLevelSku` 필드가 없습니다. 이로 인해 빈 전환 및 기타 예기치 않은 지표가 발생합니다.

* `add-to-cart` 이벤트에 `productContext` 필드가 설정되어 채워져 있지 않습니다.

* 환경 유형이 잘못되었습니다. 예를 들어 환경이 *[!UICONTROL Production]* 대신 *[!UICONTROL Testing]*(으)로 설정된 경우. 자세한 내용은 [Storefront 컨텍스트](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md)를 참조하십시오.

* [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md) 이벤트에서 검색 결과 컨텍스트가 누락되었습니다.
