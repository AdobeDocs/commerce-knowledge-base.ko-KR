---
title: 'ACSD-56447: 병렬 웹 REST API를 통해 장바구니에 동일한 제품을 추가하면 장바구니에 두 개의 개별 항목이 생성됨'
description: ACSD-56447 패치를 적용하여 병렬 웹 REST API 요청을 통해 동일한 제품을 장바구니에 추가하면 장바구니에 두 개의 개별 항목이 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447: 병렬 웹 REST API를 통해 장바구니에 동일한 제품을 추가하면 장바구니에 두 개의 개별 항목이 생성됩니다

ACSD-56447 패치는 병렬 웹 REST API 요청을 통해 동일한 제품을 장바구니에 추가하면 장바구니에 두 개의 개별 항목이 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56447입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

병렬 웹 REST API 요청을 통해 동일한 제품을 장바구니에 추가하면 장바구니에 두 개의 개별 항목이 생깁니다.

<u>재현 단계</u>:

1. [!DNL Postman]을(를) 사용하여 REST API 호출 요청을 수행하기 위한 고객 토큰을 생성합니다.
1. 고객을 위한 장바구니를 만듭니다.
1. 위에서 생성된 토큰을 사용하여 고객을 위한 빈 장바구니를 만드십시오.
1. CURL을 사용하여 두 개의 `AddProductsToCart` 요청을 동시에 실행합니다. 개발자 설명서에 있는 [주문 처리 자습서](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/)의 지침을 따릅니다.

<u>예상 결과</u>:

수량이 여러 개인 품목은 한 라인에 표시됩니다.

<u>실제 결과</u>:

동일한 SKU가 여러 라인 항목에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
