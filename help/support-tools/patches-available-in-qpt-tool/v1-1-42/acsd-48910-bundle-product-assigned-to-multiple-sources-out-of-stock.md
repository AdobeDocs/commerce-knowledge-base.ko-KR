---
title: 'ACSD-48910: 송장 및 배송 후 여러 소스가 할당된 번들 제품의 재고가 소진됨'
description: ACSD-48910 패치를 적용하면 주문이 청구되고 배송된 후 여러 소스에 할당된 번들 제품의 재고가 부족한 Adobe Commerce 문제를 해결할 수 있습니다. 아직 수량이 0이 아닌 경우에도 마찬가지입니다.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910: 송장 및 배송 후 여러 소스가 할당된 번들 제품의 재고가 소진됨

ACSD-48910 패치는 주문이 송장 발행되어 배송된 후 여러 출처에 할당된 번들 제품의 재고가 소진되는 문제를 해결합니다. 여전히 수량이 0이 아닙니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-48910입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 출처에 할당된 묶음 상품은 아직 사용 가능하더라도 인보이스 발행 및 배송 후 재고가 소진됩니다.

<u>재현 단계</u>:

1. 두 개의 웹 사이트를 만듭니다.
1. 두 개의 스토어/스토어 조회수(웹 사이트당 한 개)를 만듭니다.
1. 간단한 제품 2개(수량 = 10)를 만들어 주식과 웹 사이트 모두에 할당합니다.
1. 번들 제품을 만들고 이러한 간단한 제품을 추가합니다. 번들 제품을 두 웹 사이트에 할당합니다.
1. 상점으로 이동하여 번들 제품을 장바구니에 추가합니다.
1. 체크아웃하고 주문하십시오.
1. 관리자로부터 송장을 발행하고 주문을 출하합니다.

<u>예상 결과</u>:

10개 중 1개만 구매하여 묶음 상품은 재고가 남아 있습니다.

<u>실제 결과</u>:

번들 제품의 상태가 품절로 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
