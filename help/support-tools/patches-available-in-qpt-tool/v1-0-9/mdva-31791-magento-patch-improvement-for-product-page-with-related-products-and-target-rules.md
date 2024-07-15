---
title: 'MDVA-31791 패치: 관련 제품 및 대상 규칙을 사용한 제품 페이지 개선'
description: MDVA-31791 패치는 [관련 제품](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) 또는 [관련 제품 규칙](https://docs.magento.com/user-guide/marketing/product-related-rules.html)(대상 규칙)을 사용하는 경우 제품 페이지의 성능을 향상시킵니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-31791 패치: 관련 제품 및 대상 규칙을 사용한 제품 페이지 개선

[관련 제품](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) 또는 [관련 제품 규칙](https://docs.magento.com/user-guide/marketing/product-related-rules.html)(대상 규칙)을 사용하면 MDVA-31791 패치가 제품 페이지의 성능을 향상시킵니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치를 만들었습니다.**

클라우드 인프라의 Adobe Commerce 2.4.0

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온 클라우드 인프라 및 Adobe Commerce 온-프레미스 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관련 제품 또는 타겟 규칙을 사용하는 경우 제품 페이지의 성능이 저하됩니다.

[관련 제품](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) 또는 [관련 제품 규칙](https://docs.magento.com/user-guide/marketing/product-related-rules.html) 기능을 사용하려면 MDVA-31791 패치를 적용해 보십시오.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
