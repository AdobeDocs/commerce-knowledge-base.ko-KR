---
title: 'MDVA-34850: 취소선 인벤토리가 "0"에 도달하지 않는 견본'
description: MDVA-34850 패치는 재고가 "0"에 도달하고 PDP(Product Details Page) 링크에 표시되지 않는 견본이 연결되지 않는 문제를 해결합니다. 관리자 구성에서 **품절 제품 표시**도 *예*로 설정되어 있습니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850: 취소선 인벤토리가 &quot;0&quot;에 도달하지 않는 견본

MDVA-34850 패치는 재고가 &quot;0&quot;에 도달하고 PDP(Product Details Page) 링크에 표시되지 않는 견본이 연결되지 않는 문제를 해결합니다. 관리자 구성에서 **재고 부족 제품 표시**&#x200B;도 *예*(으)로 설정되어 있습니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.1 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기본 재고 재고가 사용되지 않고 **재고 부족 제품 표시** 구성이 활성화된 경우 재고 부족 제품 옵션이 PDP 페이지에 표시되지 않습니다.

<u>필수 구성 요소</u>:

* 다중 Source 인벤토리(MSI)를 설치합니다.
* [재고 옵션](https://docs.magento.com/user-guide/configuration/catalog/inventory.html)에서 재고 부족 제품 표시를 사용하도록 설정합니다.

<u>재현 단계</u>:

1. 모든 웹 사이트를 새 재고 \[New Stock\] 및 위의 소스에 할당하여 만듭니다. 이제 기본 재고가 사용되지 않습니다.
1. 세 가지 크기 옵션 \[S,M,L\]을 추가하여 [구성 가능한 제품을 만듭니다](https://docs.magento.com/user-guide/catalog/product-create-configurable.html).
1. 각 옵션을 열고 생성된 사용자 정의 소스 \[new\_source\]만 할당하여 수량을 추가합니다. 또한 \[Source Status\]을 \[In Stock\](으)로 설정합니다.
1. 프론트엔드에서 구성 가능한 제품을 다시 색인화하고 확인하십시오. 세 가지 옵션이 모두 표시됩니다.
1. 백엔드에서 \[size:S\]에 할당된 간단한 제품을 열고 \[Source Status\]을 \[Out of Stock\](으)로 설정하고 수량도 0으로 업데이트합니다. 프론트엔드에서 구성 가능한 제품을 다시 색인화하고 확인하십시오.

<u>예상 결과</u>:

품절 제품 표시 옵션이 활성화되어 있으므로 세 가지 옵션이 모두 표시됩니다. 품절 옵션 \[S\]을(를) 비활성화하고 제외해야 합니다. 프론트엔드 및 백엔드에 대한 주문 세부 사항에 가격 = 12x2인 2 x of 1 옵션 제품을 표시해야 합니다.

<u>실제 결과</u>:

품절 옵션이 숨겨져 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
