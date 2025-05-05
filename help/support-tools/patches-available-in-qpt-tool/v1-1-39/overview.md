---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.39에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool] (QPT) v1.1.39

이 하위 섹션에서는 [!DNL Quality Patches Tool] (QPT) v1.1.39에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.39에는 다음 패치가 포함됩니다.

1. **ACSD-53704**: 보상 포인트 만료 후 보상 포인트 잔액 기록이 잘못 계산되는 문제를 해결했습니다.
1. **ACSD-53583**: *범주 제품* 및 *제품 범주* 인덱서에 대한 부분 색인 재지정 성능을 개선합니다.
1. **ACSD-54026**: 권한이 없는 사용자에 대한 `updateCompanyRole` GraphQL 요청에 대해 잘못된 오류 메시지를 수정합니다.
1. **ACSD-54106**: 터키어 악센트 부호 문자에 대한 이름별 범주 제품 정렬이 올바르지 않은 문제를 해결했습니다.
1. **ACSD-52219**: 책갈피 보기 사이를 자주 전환할 때 관리 그리드에 저장된 필터가 예상대로 작동하지 않는 문제를 해결했습니다.
1. **ACSD-54342**: 올바른 데이터가 없는 CSV 파일을 가져올 때 데이터 구조에 잘못된 오류 메시지 *오류: 값이 혼합됨*.
1. **ACSD-54660**: GraphQL에서 고객 주문을 `sort_field` 및 `sort_direction`별로 정렬하기 위해 새 입력 특성 *sort*&#x200B;을(를) 추가했습니다.
1. **ACSD-54776**: 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 선택되지 않은 *[!UICONTROL Use Default Value]* 및 기본값이 아닌 제품 필드 값이 저장되지 않는 문제를 해결했습니다.
1. **ACSD-53998**: 고객 계정에서 로그아웃한 후 **[!UICONTROL Customer Segment]**&#x200B;을(를) 기반으로 하는 **[!UICONTROL Dynamic Block]**&#x200B;이(가) 제대로 작동하지 않는 문제를 해결했습니다.
1. **ACSD-53204**: 수정 사항 *제품을 저장할 수 없습니다.`rest/V1/products/<sku>/media` 끝점을 사용하여 제품 갤러리에 이미지를 추가하도록 동시에 요청할 때* 오류가 발생했습니다.
1. **ACSD-47657**: AWS 자격 증명에 대한 캐싱 메커니즘을 추가했습니다. 이제 자격 증명 공급자는 Magento 캐시를 사용하여 EC2 구성을 위해 AWS에서 검색한 자격 증명을 캐시합니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
