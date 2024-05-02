---
title: 'Adobe Commerce 2.3.6: 주소 저장에 무한 회전자가 표시됨'
description: 이 문서에서는 상점의 내 계정에 주소를 저장할 때 대기 중인 회전자가 무기한 표시되는 알려진 Adobe Commerce 2.3.6 문제에 대해 설명합니다.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6: 주소 저장에 무한 회전자가 표시됨

이 문서에서는 상점의 내 계정에 주소를 저장할 때 대기 중인 회전자가 무기한 표시되는 알려진 Adobe Commerce 2.3.6 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Vertex 통합이 활성화된 Adobe Commerce 2.3.6(Firefox 브라우저만 해당)

## 문제

상점의 내 계정 섹션에 주소를 저장할 때 Vertex 코어 JS의 오류로 인해 대기 중인 회전자가 무기한 표시되는 경우가 있습니다.

## 해결 방법

해결 방법: Firefox에 대한 대체 브라우저를 사용합니다.

이 문제는 Adobe Commerce 2.3.1에서 해결되었습니다.

## 관련 읽기

* [VertexAddress Cleaning을 사용하여 &#39;내 청구 및 배송 주소가 동일&#39;을 선택 해제할 때 다른 주소가 허용되지 않음](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) 을 참조하십시오.
* [Adobe Commerce 2.4.1 Vertex Address 유효성 검사 메시지 주소 업데이트 이후](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) 을 참조하십시오.
