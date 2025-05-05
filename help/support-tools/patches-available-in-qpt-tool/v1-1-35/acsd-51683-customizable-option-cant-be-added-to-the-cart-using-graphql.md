---
title: 'ACSD-51683: 사용자 지정 가능한 옵션은 GraphQL을 사용하여 장바구니에 추가할 수 없습니다.'
description: ACSD-51683 패치를 적용하여 사용자 지정 가능한 옵션을 GraphQL을 사용하여 장바구니에 추가할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: 사용자 지정 가능한 옵션은 GraphQL을 사용하여 장바구니에 추가할 수 없습니다.

ACSD-51683 패치는 사용자 지정 가능한 옵션을 GraphQL을 사용하여 장바구니에 추가할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51683입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 가능한 옵션은 GraphQL을 사용하여 장바구니에 추가할 수 없습니다.

<u>재현 단계</u>:

1. 사용자 지정 가능한 **텍스트 필드** 옵션을 사용하여 간단한 제품을 만드십시오.
1. [장바구니에 추가](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) GraphQL을 통해 사용자 지정 가능한 필수 옵션이 있는 제품을 만들었습니다.
1. [장바구니](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL 요청을 보내 장바구니에서 제품 및 제품 세부 정보를 확인합니다.

<u>예상 결과</u>

GraphQL 응답의 `Customizable_options` 섹션에는 제품을 장바구니에 추가하는 동안 제공된 데이터가 포함됩니다.

<u>실제 결과</u>

GraphQL 응답의 `Customizable_options` 섹션이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
