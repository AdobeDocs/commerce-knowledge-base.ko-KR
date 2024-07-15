---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.0.13에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool](QPT) v1.0.13 개요

이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.0.13에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.0.13에는 다음 패치가 포함됩니다.

1. **MCP-87**: 큰 프로필에 대한 범주 제품 및 주식 인덱서의 색인 지정 시간이 개선되었습니다.
1. **MDVA-13203**: 전체 색인 재지정 후 *무결성 제한 위반 search_tmp_ table* 오류가 표시되는 문제를 해결했습니다.
1. **MDVA-19391**: `catalog_category_entity_text` 테이블의 NULL 설명 레코드로 인해 `analytics_collect_data`에서 오류가 발생하는 문제를 해결했습니다.
1. **MDVA-20376**: 주문 배치 후 로그인한 고객의 경우 `exception.log`에서 *customerId = 1*&#x200B;인 엔터티가 없는 문제를 해결했습니다.
1. **MDVA-22150**: 장바구니에서 구성 가능한 제품을 사용하고 쿠폰을 적용한 고객이 해당 구성 가능한 제품을 관리자에서 사용하지 않도록 설정한 경우 로그인할 수 없는 문제를 해결했습니다.
1. **MDVA-23426**: Adobe Commerce에서 보낸 알림 전자 메일에 첨부 파일로 추가되는 내용이 포함된 빈 본문이 있는 문제를 해결했습니다.
1. **MDVA-23764**: 동적 블록의 표시에 영향을 주는 `JsFooterPlugin.php`의 버그를 수정했습니다.
1. **MDVA-30858**: **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** Settlement에서 [!DNL PayPal] Settlement 보고서를 예상대로 사용할 수 없는 문제를 해결했습니다.
1. **MDVA-32545**: 관리자로부터 주문을 만들 때 송장이 자동으로 전송되지 않는 문제를 해결했습니다.
1. **MDVA-32714**: GraphQL 제품 쿼리에서 고객 그룹 가격이 작동하지 않는 문제를 해결했습니다.
1. **MDVA-33106**: cron `run` 명령을 실행한 후 다시 예약된 제품 변경 내용이 지워지는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
