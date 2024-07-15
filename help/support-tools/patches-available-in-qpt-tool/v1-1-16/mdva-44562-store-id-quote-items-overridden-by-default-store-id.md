---
title: 'MDVA-44562: 기본 스토어 ID로 재정의된 견적 항목의 스토어 ID'
description: MDVA-44562 패치는 기본 스토어 ID가 GraphQL 요청에 대한 견적 항목에 대한 스토어 ID를 무시하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44562입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: 기본 스토어 ID로 재정의된 견적 항목의 스토어 ID

MDVA-44562 패치는 기본 스토어 ID가 GraphQL 요청에 대한 견적 항목에 대한 스토어 ID를 무시하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44562입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

견적 항목의 스토어 ID가 GraphQL 요청의 기본 스토어 ID로 재정의됩니다.

<u>재현 단계</u>:

1. 새 스토어 뷰를 만듭니다.
1. 스토어 보기당 이름이 다른 간단한 새 제품을 만듭니다.
1. 새 고객을 만듭니다.
1. 고객 인증 토큰을 얻습니다.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. 인증 토큰을 사용하여 고객에 대한 새 견적을 만듭니다.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. 장바구니에 제품을 추가합니다.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. 기본 스토어 보기에 대한 장바구니 콘텐츠를 가져옵니다.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. 새 스토어 보기에 대한 장바구니 콘텐츠를 가져옵니다.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>예상 결과</u>:

새 스토어 보기의 응답은 새 스토어 보기의 제품 이름을 표시합니다.

<u>실제 결과</u>:

새 스토어 보기의 응답은 기본 스토어 보기 아래에 제품 이름 설정을 표시합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
