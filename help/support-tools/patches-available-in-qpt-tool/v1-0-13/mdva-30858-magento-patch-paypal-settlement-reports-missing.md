---
title: 'MDVA-30858: PayPal 결제 보고서 누락'
description: "MDVA-30858 패치는 여러 PayPal 계정이 있을 때 누락된 PayPal 결제 보고서를 수정합니다. 보고서는 관리 사이드바 &gt; **보고서** &gt; 영업 &gt; **PayPal 결제**에서 사용할 수 있습니다. 대신 *레코드를 찾을 수 없습니다.* 표시됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치된 경우 사용할 수 있습니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: PayPal 결제 보고서 누락

MDVA-30858 패치는 여러 PayPal 계정이 있을 때 누락된 PayPal 결제 보고서를 수정합니다. 보고서는 관리 사이드바 > **보고서** > 판매 > **PayPal 결제**&#x200B;에서 사용할 수 있습니다. 대신 *레코드를 찾을 수 없습니다.*&#x200B;이(가) 표시됩니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.4

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

PayPal 계정이 여러 개 있는 경우 **보고서** > 판매 > **PayPal 결제**&#x200B;에서 레코드를 찾을 수 없는 문제를 해결했습니다.

<u>재현 단계</u>:

1. PayPal 결제 보고서를 구성합니다.
1. 관리자로 이동하여 **보고서** > 판매 > **PayPal 결제**&#x200B;로 이동합니다.
1. 최신 업데이트를 보려면 오른쪽 상단의 **업데이트 가져오기**&#x200B;를 클릭합니다.

<u>예상 결과</u>:

보고서가 표시됩니다.

<u>실제 결과</u>:

보고서를 사용할 수 있어도 그리드에 아무 것도 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
