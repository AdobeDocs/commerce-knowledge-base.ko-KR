---
title: Adobe Commerce 2.4.1 Vertex Address 유효성 검사 메시지 주소 업데이트 이후
description: 이 문서에서는 청구 주소와 다른 배송 주소를 사용하는 경우 결제 단계 중에 꼭지점 주소 유효성 검사가 작동하지 않는 알려진 Adobe Commerce 2.4.1 문제에 대해 설명합니다. 이 문제는 Adobe Commerce 2.4.2에서 수정될 예정입니다.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Vertex Address 유효성 검사 메시지 주소 업데이트 이후

이 문서에서는 청구 주소와 다른 배송 주소를 사용하는 경우 결제 단계 중에 꼭지점 주소 유효성 검사가 작동하지 않는 알려진 Adobe Commerce 2.4.1 문제에 대해 설명합니다. 이 문제는 Adobe Commerce 2.4.2에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

* Vertex 통합이 활성화된 Adobe Commerce 온-프레미스 2.4.1
* Vertex 통합이 활성화된 클라우드 인프라 2.4.1의 Adobe Commerce

## 문제


<u>재현 단계:</u>

1. 계정을 만들고 로그인합니다.
1. **장바구니에 추가**&#x200B;를 클릭하여 장바구니에 항목을 추가합니다. 장바구니 아이콘을 클릭한 다음 **체크아웃으로 진행**&#x200B;을 클릭합니다.
1. **배송 주소** 필드에 올바른 주소를 입력하십시오.
1. **배송 방법**&#x200B;의 옵션 중 하나를 선택하십시오. **다음**&#x200B;을 클릭합니다.
1. 주소 유효성 검사에서 다른 주소 정보를 제안하는 경우 **주소 업데이트**&#x200B;를 클릭하고 **다음**&#x200B;을 클릭합니다.
1. **내 청구 주소와 배송 주소가 동일합니다** 확인란의 선택을 취소합니다.

<u>첫 번째 시나리오:</u>

[6단계 이상](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth)을(를) 수행한 다음:

1. 유효한 새 청구 주소를 입력하십시오.
1. **업데이트** 단추를 클릭합니다. 메시지/제안을 다음과 같이 표시합니다. *주소가 잘못되었습니다.* 다음은 다음과 같은 주소 제안 사항입니다. *우편 번호: XXXXX- XXXX 거리: XXX 도시 거리 XXX*
1. **업데이트** 단추를 클릭합니다(Vertex 주소 제안의 **주소 업데이트** 단추를 클릭하지 마십시오).
1. 업데이트된 청구 주소의 **편집** 버튼을 클릭합니다.
1. 주소에서 주소를 선택합니다 드롭다운을.
1. **업데이트** 단추를 클릭합니다.

<u>예상 결과:</u>

이전 유효성 검사 메시지/제안 메시지가 제거됩니다.

<u>실제 결과:</u>

유효성 확인 메시지/제안 *&quot;유효한 주소를 찾지 못했습니다. 우편 번호: XXXXX-XXXX Street: XXX City Street XXX&quot;* 메시지가 **제거되지 않았습니다**. 양식에 잘못된 주소를 입력하면 동일한 문제가 발생합니다.

<u>두 번째 시나리오:</u>

[6단계 이상](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth)을(를) 수행한 다음:

1. 주소 양식에 유효한 주소를 입력하십시오.
1. **업데이트** 단추를 클릭합니다. 메시지/제안을 다음과 같이 표시합니다. *주소가 잘못되었습니다.* 다음에 *우편 번호: XXXXX-XXXX 거리: XXX 도시 거리 XXX*&#x200B;와 같은 주소 제안을 제공합니다.
1. **업데이트** 단추를 클릭합니다(꼭지점 주소 제안의 **주소 업데이트** 단추를 클릭하지 마십시오).
1. ***내 청구 및 배송 주소가 동일한지*** 드롭다운을 확인하세요.

<u>예상 결과:</u>

이전 유효성 검사 메시지/제안 메시지가 제거됩니다.

<u>실제 결과:</u>

유효성 확인 메시지/제안 *&quot;유효한 주소를 찾지 못했습니다. 우편 번호: XXXXX-XXXX Street XXX City street XXX&quot;* 메시지가 **제거되지 않았습니다**. 양식에 잘못된 주소를 입력하면 동일한 문제가 발생합니다.

## 지원 기술 자료의 관련 자료:

[Adobe Commerce 2.3.6, 2.4.0-p1 및 2.4.1 알려진 문제: 계정이 활성화되면 dotdigital에 로그인할 수 없음](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
