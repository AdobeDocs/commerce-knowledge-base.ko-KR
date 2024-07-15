---
title: 'MDVA-30565: 세션 캐시 로컬 저장소 및 체크아웃 문제'
description: MDVA-30565 패치는 세션 캐시 로컬 저장소 및 체크아웃 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우 사용할 수 있습니다.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565: 세션 캐시 로컬 저장소 및 체크아웃 문제

MDVA-30565 패치는 세션 캐시 로컬 저장소 및 체크아웃 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 세션이 시간 초과된 경우에도 장바구니 항목을 장바구니 페이지에 계속 볼 수 있습니다. 이로 인해 게스트 체크아웃에 사용할 수 있는 배송 방법이 없는 예상 배송 방법 오류가 발생합니다.

<u>재현 단계</u>:

1. Commerce 관리자에서 영구 장바구니를 활성화합니다. (**지속성 사용** = &quot;*예*&quot;)
1. 프론트엔드에 고객으로 로그인합니다. `persistent_shopping_cart` 쿠키를 만들고 영구 세션을 시작합니다.
1. 장바구니에 제품을 추가합니다.
1. 프론트엔드 세션이 시간 초과될 때까지 기다리거나 `PHPSESSID` 쿠키를 삭제하십시오.
1. 이제 게스트 사용자이지만 장바구니로 이동하더라도 로그인 고객으로 추가된 제품을 확인할 수 있습니다.
1. 장바구니에서 제품을 제거하면 이제 장바구니가 비어 있습니다. 이 이벤트에서 Adobe Commerce이 `persistent_shopping_cart` 쿠키를 삭제하는 것을 볼 수 있습니다.
1. 장바구니에 새 제품을 추가하고 장바구니 페이지로 이동합니다.
1. 이제 브라우저 콘솔에서 `V1/guest-carts/4/estimate-shipping-methods` 요청이 `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}` 메시지와 함께 404 응답을 반환합니다.

<u>예상 결과</u>:

예상 배송 방법 요청이 올바른 결과를 반환합니다.

<u>실제 결과</u>:

&quot;*죄송합니다. 현재 이 주문에 대해 견적을 사용할 수 없습니다.*&quot;과(와) 같은 오류가 발생하여 예상 배송 방법 요청이 실패합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
