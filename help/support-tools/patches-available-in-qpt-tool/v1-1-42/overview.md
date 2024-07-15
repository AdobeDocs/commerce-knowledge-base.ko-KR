---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.42에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool](QPT) v1.1.42

이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.1.42에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.42에는 다음 패치가 포함됩니다.

1. **ACSD-53658**: 스토어 보기에서 *[!UICONTROL Recently Viewed]* 제품 데이터가 제대로 업데이트되지 않는 문제를 해결했습니다.
1. **ACSD-54626**: GraphQL을 통해 `NUMBER_OF_SKUS` 특성이 있는 새 구매 주문 규칙(`createPurchaseOrderApprovalRule`)을 만들 수 없는 문제를 해결했습니다.
1. **ACSD-53845**: `consumer max_messages` = 0일 때 MySQL 연결 시간 초과 문제를 해결했습니다.
1. **ACSD-54890**: `/tmp` 디스크의 공간이 부족하여 `aggregate_sales_report_bestsellers_data`에서 MySQL 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-55112**: [!DNL Google reCAPTCHA v3] 유효성 검사 없이 *[!UICONTROL Submit review]* 단추를 여러 번 클릭할 수 있는 문제를 해결했습니다.
1. **ACSD-54264**: 오류 메시지 *요청한 특성을 업데이트할 수 없는 문제를 해결했습니다. 행 ID: store_id*&#x200B;은 고객이 다른 스토어 보기에서 협상 가능한 견적을 사용하여 체크아웃하려고 할 때 표시됩니다.
1. **ACSD-54418**: 고정 할인 금액이 동적으로 가격이 책정된 번들의 각 하위 제품에 잘못 적용되는 문제를 해결했습니다.
1. **ACSD-55238**: 빈 제품 메타 설명을 저장할 때 발생하는 문제를 해결했습니다.
1. **ACSD-54966**: 이전 주문이 실패한 경우 고객당 사용이 제한된 쿠폰 코드를 다시 사용할 수 없는 문제를 해결했습니다.
1. **ACSD-54060**: 제한된 관리자가 다른 범위에 할당된 다른 제품의 하위 제품인 경우 제품을 저장할 수 없는 문제를 해결했습니다.
1. **ACSD-48910**: 주문이 청구되어 배송된 후 여러 소스에 할당된 번들 제품의 수량이 0이 아닌 경우에도 재고가 부족한 문제를 해결합니다.
1. **ACSD-55381**: GraphQL을 통해 B2B *[!UICONTROL Requisition list]*&#x200B;에서 `configurable_product_option_uid` 및 `configurable_product_option_value_uid` 필드를 쿼리할 때 내부 서버 오류를 수정합니다.
1. **ACSD-55628**: 회사 등록 양식에 파일을 업로드하고 상점 첫 화면에서 고객 특성에 대한 파일을 바꾸는 문제가 수정되었습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
