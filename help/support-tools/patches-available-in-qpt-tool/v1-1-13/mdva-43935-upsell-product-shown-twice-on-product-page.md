---
title: 'MDVA-43935: 제품 페이지에 두 번 표시된 상향 판매 제품'
description: MDVA-43935 패치는 제품 페이지에 상향 판매 제품이 두 번 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43935입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 4ca531b8-12c1-4fa1-b036-5531d11b0f1d
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-43935: 제품 페이지에 두 번 표시된 상향 판매 제품

MDVA-43935 패치는 제품 페이지에 상향 판매 제품이 두 번 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43935입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 페이지에 업셀 제품이 두 번 표시됩니다.

<u>재현 단계</u>:

1. 하위 범주를 만듭니다.
1. 간단한 제품을 만듭니다.
1. 간단한 제품을 옵션으로 사용하는 번들을 만듭니다.
1. 캐시를 플러시하고 색인 재지정을 수행합니다.
1. 상점에서 간단한 상품을 열어보세요.

<u>예상 결과</u>:

번들 제품은 업셀로 한 번만 나열됩니다.

<u>실제 결과</u>:

번들 제품이 두 번 나열됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
