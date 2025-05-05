---
title: 'ACSD-57588: 여러 주소로 배송 시 지역 ID 처리 도중 오류 발생'
description: ACSD-57588 패치를 적용하여 여러 주소로 주문을 배송하면 지역 ID 처리 중에 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Shipping/Delivery
role: Admin, Developer
source-git-commit: 1899e4601d292a8543d1c34e622251a7f6aed124
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-57588: 여러 주소로 배송 시 지역 ID 처리 도중 오류 발생

ACSD-57588 패치는 주문을 여러 주소로 배송하면 지역 ID 처리 중에 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57588입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 주소로 배송 시 지역 ID를 처리하는 동안 오류가 트리거되었습니다.

<u>재현 단계</u>:

1. [!DNL Braintree] 결제 방법을 구성하십시오.
1. 상점 첫 화면에서 고객으로 로그인합니다.
1. 장바구니에 제품을 추가하고 장바구니를 보고 편집합니다.
1. 체크아웃 프로세스 중에 *(예: 영국, 미국, CA)* 주소를 여러 개 추가하고 주문을 검토하십시오.
1. 체크아웃 페이지에서 신용 카드 결제 옵션을 선택하고 필요한 자격 증명을 입력한 다음 주문합니다.

<u>예상 결과</u>:

주문은 정상적으로 가능합니다.

<u>실제 결과</u>:

주문이 되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
