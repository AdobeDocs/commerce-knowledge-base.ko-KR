---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.50'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.50에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f62cf4284d7bb99a1ab58df676dfff726c34d327
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool](QPT) v1.1.50

이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.1.50에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.50에는 다음 패치가 포함됩니다.

1. **ACSD-59280**: 2.4.4-pX 버전을 설치할 때 정의되지 않은 메서드 ReflectionUnionType::getName()*에 대한*&#x200B;호출 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-45049**: 관리자의 웹 사이트 범위에 따라 고객 *[!UICONTROL Is required]* 특성 설정이 제대로 작동하지 않는 문제를 해결했습니다.
1. **ACSD-46938**: `setup:upgrade` 동안 DB 트리거 재생성 성능 문제를 해결했습니다.
1. **ACSD-48210**: 특정 저장소 보기에서 *[!UICONTROL website scope]* 특성을 업데이트하는 것이 전역 범위의 특성 값을 재정의하는 문제를 해결했습니다.
1. **ACSD-54887**: *[!UICONTROL Persistent Shopping Cart]*&#x200B;을(를) 사용하도록 설정한 상태에서 고객 세션이 만료된 후 고객 장바구니가 지워지는 문제를 해결했습니다.
1. **ACSD-58141**: [!UICONTROL L2 Redis cache]이(가) 활성화되고 고객이 관리에서 업데이트된 경우 로그인한 고객의 상점 영역에 대한 POST 요청에서 `PHPSESSID`이(가) 다시 발생하는 문제를 해결합니다.
1. **ACSD-58352**: 요청 헤더에 기본이 아닌 저장소 보기가 지정된 경우 기본 저장소 보기에 대한 반환 특성 레이블이 GraphQL API를 통해 반환되는 문제를 해결했습니다.
1. **ACSD-58442**: 너비가 *768px*&#x200B;인 장치가 모바일로 처리되어 메뉴 및 헤더가 데스크탑 대신 모바일 보기에서 로드되는 문제를 해결했습니다.
1. **ACSD-58790**: [!DNL Chrome]의 모바일 보기에서 제품 세부 사항 페이지 이미지에 대한 *핀치-투-줌* 기능을 수정합니다.
1. **ACSD-59036**: 하한과 상한이 모두 *$0*&#x200B;인 제품 가격을 로드할 때 발생하는 예외를 수정합니다.
1. **ACSD-59229**: 요청에서 [!UICONTROL X-Magento-Vary]의 이전 값으로 인해 고객 그룹 관련 정보가 잘못된 세그먼트에 저장되는 문제를 해결했습니다.
1. **ACSD-59378**: 가져오는 동안 저장소 수준 URL 다시 쓰기가 잘못 업데이트되는 문제를 해결했습니다.
1. **ACSD-59514**: [!DNL Page Builder]을(를) 사용하는 관리 영역의 양식에서 *[!DNL Page Builder]이(가) 잠금 해제 없이 5초 동안 렌더링되는 문제를 해결했습니다.양식을 제출한 후 브라우저 콘솔에서* 오류가 발생하여 변경 내용을 저장할 수 없습니다.
1. **ACSD-60303**: HTML 축소가 활성화된 경우 관리자의 주문을 할 수 없는 문제를 해결했습니다.
1. **ACSD-60441**: 백엔드에서 생성된 통합 액세스 토큰을 사용할 때 `V1/customers REST API` 끝점을 통해 고객을 업데이트하는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.

