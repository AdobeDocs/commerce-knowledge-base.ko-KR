---
title: 'ACSD-55566: [!UICONTROL mergeCart] 에서 내부 서버 오류로 인해 돌연변이가 실패합니다. [!DNL GraphQL] 응답'
description: ACSD-55566 패치를 적용하여 "mergeCart" 돌연변이가 실패하고 내부 서버 오류가 발생하는 Adobe Commerce 문제를 해결합니다. [!DNL GraphQL] 동일한 번들 항목이 있는 소스 장바구니와 대상 장바구니를 병합할 때의 응답입니다.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566: `mergeCart` 에서 내부 서버 오류로 인해 돌연변이가 실패합니다. [!DNL GraphQL] 응답

ACSD-55566 패치를 사용하면 다음과 같은 문제가 해결됩니다. `mergeCart` 돌연변이가 실패하고 의 내부 서버 오류가 발생합니다 [!DNL GraphQL] 응답. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치되었습니다. 패치 ID는 ACSD-55566입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`mergeCart` 돌연변이가 실패하고 의 내부 서버 오류가 발생합니다 [!DNL GraphQL] 동일한 번들 항목이 있는 소스 장바구니와 대상 장바구니를 병합할 때의 응답입니다.

<u>재현 단계</u>:

1. 사용자 지정 소스 및 사용자 지정 스톡을 만듭니다.
1. 생성된 재고를 기본 웹 사이트에 할당합니다.
1. 간단한 제품을 만들고 생성된 소스(수량=2)를 지정합니다.
1. 하나의 옵션과 하나의 하위 제품(3단계에서 만든 제품)으로 번들 제품을 만듭니다.
1. 다음을 통해 게스트 카트 만들기 [!DNL GraphQL].
1. 두 옵션을 모두 선택한 번들 제품을 추가합니다.
1. 저장 *cartID*.
1. 고객을 생성하고 고객 토큰을 생성합니다.
1. 고객 장바구니를 만듭니다.
1. 구성이 동일한 동일한 동일한 번들 제품을 장바구니에 추가합니다.
1. 게스트 카트를 고객 카트와 병합해 보십시오.

<u>예상 결과</u>:

고객 장바구니에는 두 장바구니의 제품이 포함되어 있습니다.

<u>실제 결과</u>:

내부 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
