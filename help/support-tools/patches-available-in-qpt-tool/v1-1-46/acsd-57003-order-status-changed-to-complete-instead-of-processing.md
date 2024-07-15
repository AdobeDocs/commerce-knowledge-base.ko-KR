---
title: 'ACSD-57003: *처리 중*으로 변경하는 대신 *완료*로 주문 상태가 변경됨'
description: ACSD-57003 패치를 적용하여 주문 상태가 *처리 중*으로 변경되는 대신 *완료*로 변경되는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: *처리*(으)로 변경하는 대신 주문 상태가 *완료*(으)로 변경됩니다.

ACSD-57003 패치는 주문 상태가 *처리 중*(으)로 변경되는 대신 *완료*(으)로 변경되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.46이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57003입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문이 부분적으로 환불 및 부분적으로 배송된 경우 주문 상태가 *처리 중*(으)로 변경되는 대신 *완료*(으)로 변경됩니다.

<u>재현 단계</u>:

1. 구성 가능한 두 제품을 사용하여 주문을 만듭니다.
1. 모든 항목에 대한 송장을 발행합니다.
1. 첫 번째 품목만 출하합니다.
1. 배송된 항목(*첫 번째 항목*)에 대해서만 환불/대변 메모를 만듭니다.
1. 주문 상태를 확인합니다.

<u>예상 결과</u>:

주문 상태는 _처리 중_ 상태여야 합니다.

<u>실제 결과</u>:

부분적으로 배송된 항목에 대한 대변 메모를 만든 후 주문 상태가 *완료*(으)로 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
