---
title: '[!DNL Live Search] 대시보드 및 검색 결과 순위가 올바르지 않음'
description: 이 문서에서는  [!DNL Live Search] 대시보드의 데이터가 올바르지 않거나 검색 결과의 순위가 예상과 다른 경우 문제 해결 정보를 제공합니다.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# [!DNL Live Search] 대시보드 및 검색 결과 순위가 올바르지 않음

[!DNL Live Search] 대시보드에 표시된 데이터가 올바르지 않거나 [검색 결과 순위](https://experienceleague.adobe.com/ko/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies)가 예상과 다른 경우 가능한 이유를 확인하려면 다음을 참조하십시오.

* `productView` 이벤트에 제품 컨텍스트의 `topLevelSku` 필드가 없습니다. 이로 인해 빈 전환 및 기타 예기치 않은 지표가 발생합니다.

* `add-to-cart` 이벤트에 `productContext` 필드가 설정되어 채워져 있지 않습니다.

* 환경 유형이 잘못되었습니다. 예를 들어 환경이 *[!UICONTROL Production]* 대신 *[!UICONTROL Testing]*(으)로 설정된 경우. 자세한 내용은 [Storefront 컨텍스트](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md)를 참조하십시오.

* [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md) 이벤트에서 검색 결과 컨텍스트가 누락되었습니다.
