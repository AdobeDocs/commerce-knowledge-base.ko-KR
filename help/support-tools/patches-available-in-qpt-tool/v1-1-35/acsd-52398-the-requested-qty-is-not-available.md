---
title: 'ACSD-52398: 번들 제품의 수량을 업데이트하려고 할 때 요청된 수량을 사용할 수 없음'
description: ACSD-52398 패치를 적용하여 상점 앞의 장바구니에 번들 제품의 수량을 업데이트하려고 할 때 요청된 수량을 사용할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398: 번들 제품의 수량을 업데이트하려고 할 때 요청된 수량을 사용할 수 없음

ACSD-52398 패치는 상점 앞의 장바구니에 있는 번들 제품의 수량을 업데이트하려고 할 때 요청된 수량을 사용할 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52398입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

상점 앞의 장바구니에 있는 번들 제품의 수량을 업데이트하려고 할 때 요청한 수량을 사용할 수 없습니다.

<u>재현 단계</u>:

1. 수량이 *1* 및 *10*&#x200B;인 간단한 제품 두 개를 만듭니다.
1. 간단한 제품을 사용하여 번들 제품을 만듭니다.
1. 번들 제품을 장바구니에 추가합니다.
1. 제품을 편집하고 *10*&#x200B;개 항목을 사용할 수 있는 옵션의 수량을 *3*(으)로 업데이트해 보세요.

<u>예상 결과</u>:

오류가 없습니다. 이 옵션에 대한 재고가 *10*&#x200B;개 있으므로 수량을 성공적으로 업데이트했습니다.

<u>실제 결과</u>:

다음 오류가 발생합니다. *요청한 수량을 사용할 수 없습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
