---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.48에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool] (QPT) v1.1.48

이 하위 섹션에서는 [!DNL Quality Patches Tool] (QPT) v1.1.48에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.48에는 다음 패치가 포함됩니다.

1. **ACSD-55566**: 원본 및 대상 카트의 번들 항목이 같을 때 GraphQL 응답에서 *[!UICONTROL mergeCart mutation]*&#x200B;이(가) *내부 서버 오류*&#x200B;와 함께 실패하는 문제를 해결했습니다.
1. **ACSD-56546**: *[!UICONTROL Display Out of Stock Product]* 구성을 사용하지 않도록 설정할 때 구성 가능한 제품과 번들 제품이 상점 앞에 *[!UICONTROL Out of Stock]*(으)로 표시되는 문제를 해결했습니다.
1. **ACSD-56635**: 가져오기를 사용할 때 가져온 고객이 동일한 전자 메일 주소로 복제되고 [!UICONTROL Account Sharing]이(가) *[!UICONTROL Global]*(으)로 설정된 문제를 해결했습니다.
1. **ACSD-56741**: 데이터베이스에 인덱스 메커니즘 및 [!DNL MView]과(와) 관련이 없는 사용자 지정 MySQL 트리거가 포함되어 있을 때 `setup:upgrade` 동안 표시되는 *null 형식의 값에 대한 배열 오프셋에 액세스하려고 시도함* 오류 메시지를 수정합니다.
1. **ACSD-57315**: [!UICONTROL Admin]의 트랜잭션 보기 화면에서 **[!UICONTROL Fetch]** 단추를 클릭할 때마다 [!DNL PayPal Payflow Pro]에서 새 트랜잭션이 만들어지는 문제를 해결했습니다.
1. **ACSD-57337**: 특정 웹 사이트에 대한 액세스 제한이 있는 관리자가 *[!UICONTROL Companies]* 그리드의 모든 웹 사이트에서 회사를 볼 수 있는 문제를 해결했습니다.
1. **ACSD-57394**: GraphQL의 여러 정렬 필드를 기준으로 잘못된 제품 정렬을 수정합니다.
1. **ACSD-57565**: 기간이 업데이트될 때까지 *[!UICONTROL Order]* 대시보드에 잘못된 주문 정보가 표시되는 문제를 해결했습니다. 이제 대시보드에 첫 번째 로드 시 올바른 주문 통계가 표시됩니다.
1. **ACSD-57854**: 제품 GraphQL 요청이 범주 집계에서 비활성화된 범주를 반환하는 문제를 해결했습니다.
1. **ACSD-58008**: 종료 날짜가 지정되지 않은 경우 예약된 업데이트를 업데이트하면 준비된 항목의 이전 버전이 제거되는 문제가 해결되었습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.

