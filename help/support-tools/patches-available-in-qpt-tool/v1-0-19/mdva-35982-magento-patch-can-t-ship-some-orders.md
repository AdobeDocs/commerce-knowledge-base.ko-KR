---
title: "MDVA-35982: 일부 주문을 배송할 수 없음"
description: MDVA-35982 패치는 특정 웹 사이트로 제한된 관리 사용자가 동일한 웹 사이트에 배치된 주문에 대한 납품을 생성할 수 없는 경우 오류를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-35982입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982: 일부 주문을 배송할 수 없음

MDVA-35982 패치는 특정 웹 사이트로 제한된 관리 사용자가 동일한 웹 사이트에 배치된 주문에 대한 납품을 생성할 수 없는 경우 오류를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-35982입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

상인은 특정 주문을 출하할 수 없습니다.

<u>재현 단계</u>:

1. 기본 스토어를 제외한 제품에 대한 제품 웹 사이트를 선택합니다. 자세한 단계는 사용 안내서의 [웹 사이트의 제품](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html)을 참조하십시오.
1. 기본 웹 사이트/저장소가 선택되지 않은 사용자 지정 역할 범위가 있는 관리자의 사용자 역할을 만듭니다. 자세한 단계는 사용 안내서의 [역할 정의](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role)를 참조하십시오.
1. 편집 모드에서 제품을 열고 **고급 가격**&#x200B;에서 이 제품에 대한 그룹 가격을 설정합니다. 자세한 단계는 사용 안내서의 [그룹 가격](https://docs.magento.com/user-guide/catalog/product-price-group.html)을 참조하세요.
1. 이 제품으로 주문을 만듭니다.
1. 이 사용자 역할로 관리자 아래에 로그인하고 배송을 만듭니다. 자세한 단계는 사용 안내서의 [배송 만들기](https://docs.magento.com/user-guide/sales/shipments-create.html)를 참조하십시오.

<u>예상 결과</u>:

선적이 생성됩니다.

<u>실제 결과</u>:

다음 오류가 표시됩니다.

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
