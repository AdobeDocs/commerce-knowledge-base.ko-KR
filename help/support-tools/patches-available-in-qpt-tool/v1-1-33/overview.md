---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.33에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool](QPT) v1.1.33

이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.1.33에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.33에는 다음 패치가 포함됩니다.

1. **ACSD-50478**: DB 덤프에 트리거와 구분 기호 SQL 명령이 포함된 경우에 대한 데이터베이스 rollback 명령을 수정합니다.
1. **ACSD-50512**: 오류를 수정합니다. *다운로드 가능한 링크가 제품과 관련이 없습니다. 링크를 확인하고 다시 시도하십시오.다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 발생하는*
1. **ACSD-50949**: SKU 필터에 사용할 때 [!UICONTROL Advanced Search]의 가격 필터가 적절한 결과를 반환하지 않는 문제를 해결했습니다.
1. **ACSD-51645**: 확장 `Magento_OfflineShipping`을(를) 사용하지 않도록 설정한 경우 새 [!UICONTROL Cart Price Rule]을(를) 저장할 때 throw되는 오류를 수정합니다.
1. **ACSD-50895**: [!DNL Google Analytics] 4 GTM이 구성되지 않은 경우 [!DNL Google Analytics] 3 GTM 태그가 실행되지 않는 문제가 해결되었습니다.
1. **ACSD-51102**: 예약된 업데이트로 규칙을 사용하도록 설정한 경우 많은 수의 제품에 적용되는 카탈로그 규칙이 올바르게 인덱싱되지 않는 문제를 해결했습니다.
1. **ACSD-50368**: 비동기 REST API 또는 비동기 벌크 REST API를 통해 고객을 만들 때 고객의 `group_id`이(가) 무시되는 문제를 해결합니다.
1. **ACSD-51497**: 고객이 드롭다운 유형의 [!UICONTROL Custom Attribute]을(를) 기준으로 카탈로그 페이지를 정렬할 수 없는 문제를 해결했습니다.
1. **ACSD-51408**: 주문 항목 상태가 [!UICONTROL Backordered](으)로 잘못 설정된 문제를 해결했습니다.
1. **ACSD-51735**: 제품 재고가 *0*&#x200B;일 때 주문 항목 상태가 [!UICONTROL Ordered](으)로 잘못 설정되는 문제가 수정되었습니다.
1. **ACSD-51792**: [!DNL Google Tag Manager] 4를 사용하도록 설정한 경우 페이지에 노출 이벤트가 없는 문제를 해결했습니다.
1. **ACSD-51471**: 관리자가 자체적으로 예약된 업데이트가 있는 간단한 제품을 사용하는 번들 제품에 대해 예약된 업데이트를 저장할 수 없는 문제를 해결했습니다.
1. **ACSD-51700**: 관리자의 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환할 때 발생하는 오류를 수정합니다.
1. **ACSD-51120**: 스테이징 업데이트를 통해 업데이트된 CMS 블록이 포함된 CMS 페이지에 대해 GraphQL GET 요청 캐시가 지워지지 않는 문제를 해결했습니다.
1. **ACSD-51240**: 회사 등록 양식을 통해 등록한 경우 업로드된 파일이 없는 문제를 수정합니다.
1. **ACSD-51907**: 제한된 관리자가 오프라인 환불로 대변 메모를 만들 수 없는 문제를 해결했습니다.
1. **ACSD-52148**: [!UICONTROL Google V3 reCAPTCHA Admin] 로그인이 가끔 실패하는 문제를 해결했습니다.
1. **ACSD-51431**: 변경 로그에 새 항목이 없는 경우에도 인덱서 상태가 작동하는 문제를 해결했습니다.
1. **ACSD-51892**: 배포 중에 구성 파일이 여러 번 로드되는 성능 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
