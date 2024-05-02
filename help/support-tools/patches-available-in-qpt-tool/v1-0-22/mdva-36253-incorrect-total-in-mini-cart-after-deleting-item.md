---
title: 'MDVA-36253: 항목을 삭제한 후 미니 장바구니의 합계가 잘못됨'
description: MDVA-36253 패치는 다중 배송 체크아웃 단계를 사용할 때 제품을 삭제한 후 미니 장바구니 페이지로 돌아가면 제품 가격이 업데이트되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36253입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: cbd436d7-7fbd-46dd-97cf-30f709da1ce5
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-36253: 항목을 삭제한 후 미니 장바구니의 합계가 올바르지 않음

MDVA-36253 패치는 다중 배송 체크아웃 단계를 사용할 때 제품을 삭제한 후 미니 장바구니 페이지로 돌아가면 제품 가격이 업데이트되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치되어 있습니다. 패치 ID는 MDVA-36253입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.0-2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

항목을 삭제한 후 미니 장바구니의 합계가 잘못되었습니다.

<u>재현 단계</u>:

1. 하나 이상의 주소가 있는 고객으로 로그인합니다.
1. 장바구니에 4개의 제품을 추가합니다(가격 = 10달러).
1. 장바구니로 이동하고 **여러 주소로 체크아웃**.
1. 항목 하나를 제거합니다.
1. 홈 페이지로 돌아갑니다.
1. 장바구니를 열고 총 가격을 확인합니다.

<u>예상 결과</u>:

총 30달러입니다

<u>실제 결과</u>:

총 40달러입니다

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
