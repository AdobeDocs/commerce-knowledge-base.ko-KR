---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.0.7에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool](QPT) v1.0.7 개요

이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.0.7에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.0.7에는 다음 패치가 포함됩니다.

1. **MDVA-29148**: API 호출을 통해 제품을 만들 때 페이로드에 값이 제공되지 않은 경우 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 유형의 제품 사용자 지정 특성(예: Multiselect)이 기본값을 사용하지 않는 문제를 해결했습니다.
1. **MDVA-29389**: `analytics_collect_data` cronjob에 *Port가 호스트 매개 변수(예: localhost:3306)* 내에 구성되어야 한다고 표시되는 고급 보고와 관련된 문제를 해결했습니다.
1. **MDVA-30594**: FPT를 구성할 때 체크아웃 중에 여러 주소가 있는 주문을 저장할 수 없는 문제를 해결했습니다.
1. **MDVA-30782**: 장바구니 규칙과 관계없이 동적 블록이 표시되는 문제를 해결했습니다.
1. **MDVA-30815**: 검색 결과 페이지에 표시할 검색 결과의 수를 변경할 때 발생하는 문제를 해결했습니다.
1. **MDVA-30837**: 사용자가 소계(또는 총계)를 기준으로 무료 배송을 받기 위해 최소 주문 금액을 구성할 수 있도록 무료 배송 계산에 대한 구성 옵션을 추가합니다.
1. **MDVA-30945**: 장바구니 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`을(를) 업데이트할 때 치명적인 오류 메시지가 표시되는 문제를 해결했습니다.
1. **MDVA-30972**: WebApi를 사용하여 부분 선적을 만든 후 사용자 지정 주문 상태가 *처리*(으)로 변경된 문제를 해결했습니다.
1. **MDVA-31007**: 사용자 지정 주소 특성이 내 계정 영역 및 백엔드의 순서 정보 페이지에 올바르게 표시되지 않는 문제를 해결했습니다.
1. **MDVA-31021**: `module-catalog-import-export/Model/Import/Product/Option.php`에서 성능 문제가 발생하는 문제를 해결했습니다. `catalog_product_option` 테이블에 ~100k개 이상의 레코드가 있는 경우 단일 제품을 사용하는 새 CSV의 유효성을 검사하는 데 10초 미만이 소요됩니다.
1. **MDVA-31224**: 번들 제품에 대한 `catalog_product_price` 다시 인덱싱 작업의 성능을 개선합니다.
1. **MDVA-31282**: Adobe Commerce의 [!DNL Paypal PayFlow Pro]에서 두 번의 승인이 발생하는 문제를 해결했습니다. 이중 허용은 [!DNL PayFlow Pro's] 사기 필터를 우회하고 거래 수수료를 두 배로 늘리는 효과도 있습니다.
1. **MDVA-31343**: 범주가 예약되어 있을 때 제거된 본문 클래스 `page-layout-category-full-width`의 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
