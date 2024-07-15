---
title: "MDVA-34943: 빠른 주문에서 장바구니에 2개 이상의 제품을 추가할 수 없음"
description: MDVA-34943 패치는 빠른 주문으로 장바구니에 제품을 두 개 이상 추가할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943: 빠른 주문에서 장바구니에 2개 이상의 제품을 추가할 수 없음

MDVA-34943 패치는 빠른 주문으로 장바구니에 제품을 두 개 이상 추가할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.0-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 두 개 이상의 제품을 빠른 순서로 추가할 수 없습니다.

<u>필수 구성 요소</u>:

간단한 제품이 포함된 Adobe Commerce.

<u>재현 단계</u>:

1. 로그인하지 않은 상태에서 Storefront의 **빠른 주문**(으)로 이동합니다.
1. 올바른 SKU를 입력하고 자동 완성 필드에 표시되는 제품을 클릭한 다음 **수량** = *1*&#x200B;을(를) 설정합니다.
1. 같은 유효한 SKU를 입력하되, 첫 문자의 대/소문자를 변경하고(대문자를 소문자로 변경하거나 소문자를 대문자로 변경), 자동 완성 필드에 표시되는 제품을 클릭하고 **Quantity** = *1*&#x200B;을(를) 설정합니다.
1. **SKU**&#x200B;에 대한 `random_sting_value`을(를) 입력하고 **수량** = *1*&#x200B;을(를) 설정합니다.
1. **SKU** = *123123123*&#x200B;을(를) 설정하고 **Quantity** = *1*&#x200B;을(를) 설정합니다.
1. **빠른 주문** 페이지에 추가한 첫 번째 항목을 제외한 모든 항목을 삭제합니다.
1. **여러 SKU 입력** 필드에 첫 번째 SKU(위의 2단계와 유사)를 입력하고 **목록에 추가**&#x200B;를 클릭합니다.
1. 이렇게 하면 첫 번째 SKU는 2개, `random_sting_value`은(는) 한 줄의 수량이 됩니다.
1. 더 테스트하려면 페이지를 새로 고칩니다.
1. 이렇게 하면 예상대로 빠른 주문에 대한 SKU가 없습니다.
1. **여러 SKU 입력** 필드에 `random_sting_value2`을(를) 입력하고 **목록에 추가**&#x200B;를 클릭합니다.
1. 이렇게 하면 이전에 두 개의 유효한 SKU와 `random_sting_value2`이(가) 생성됩니다.

<u>예상 결과</u>:

예상대로 둘 이상의 제품을 장바구니에 추가할 수 있습니다.

<u>실제 결과</u>:

**장바구니** 페이지로 이동하면 처음 추가된 제품이 정상적으로 표시되지만, 두 번째 제품과 장바구니에 추가된 후속 제품의 경우 &quot;*1 제품에 주의가 필요합니다*&quot; 오류 메시지가 표시됩니다. 두 번째 또는 다른 추가 제품은 **장바구니** 페이지의 **제품 주의 필요** 섹션에 나열됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
