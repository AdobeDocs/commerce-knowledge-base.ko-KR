---
title: "MDVA-33704 패치: 매장 내 픽업이 표시되지 않음"
description: MDVA-33704 패치는 매장 픽업 옵션이 있는 제품이 배송 방법으로 표시되지 않는 문제를 해결합니다.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-33704 패치: 매장 내 픽업이 표시되지 않음

MDVA-33704 패치는 매장 픽업 옵션이 있는 제품이 배송 방법으로 표시되지 않는 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-33704입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** 클라우드 인프라 2.4.0-p1

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.0-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소</u>:<br>

**스토어에서 선택** 사용

<u>재현 단계</u>:

1. 장바구니에 제품을 추가합니다.
1. 체크아웃으로 이동합니다.
1. 배송 정보를 추가하고 매장 픽업 이외의 배송 방법을 선택합니다.
1. **결제 진행**&#x200B;을 선택한 후 결제 페이지로 진행하지 마십시오.
1. 대신 **연락처 및 배송** 섹션으로 돌아가십시오.
1. **Pickup**&#x200B;을(를) 선택하십시오.
1. **스토어**&#x200B;를 선택하고 **결제하려면 클릭**&#x200B;하세요.
1. 배송 주소는 자동으로 청구 주소로 입력됩니다.
1. 웹 페이지를 새로 고칩니다.

<u>예상 결과</u>:

예상대로 매장 픽업 옵션이 배송 방법으로 표시됩니다.

<u>실제 결과</u>:

매장 픽업 옵션은 배송 방법으로 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
