---
title: 'ACSD-51471: 관리자가 번들 제품에 대해 예약된 업데이트를 저장할 수 없음'
description: ACSD-51471 패치를 적용하여 관리자가 업데이트가 예약된 간단한 제품을 사용하는 번들 제품에 대해 예약된 업데이트를 저장할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: 7d80aef0-8505-4491-bde3-5b1a30b840f6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51471: 관리자가 번들 제품에 대해 예약된 업데이트를 저장할 수 없음

ACSD-51471 패치는 관리자가 업데이트가 예약된 간단한 제품을 사용하는 번들 제품에 대해 예약된 업데이트를 저장할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51471입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자는 자신에게 예약된 업데이트가 있는 간단한 제품을 사용하는 번들 제품에 대해 예약된 업데이트를 저장할 수 없습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. *시작 날짜*&#x200B;만 있고 *종료 날짜*&#x200B;는 없는 간단한 제품에 대해 예약된 업데이트를 추가합니다.
1. 업데이트가 적용된 후 제품의 SKU를 변경합니다.
1. 번들 제품을 만들고 1단계에서 만든 간단한 제품을 하위 제품으로 추가합니다.
1. 번들 제품에 대한 예정된 업데이트를 만들어 번들 제품을 활성화합니다. 예약된 업데이트에 *시작 날짜*&#x200B;와(과) *종료 날짜*&#x200B;를 모두 제공하십시오.
1. 예약된 업데이트를 저장합니다.

<u>예상 결과</u>:

예약된 업데이트가 정상적으로 저장되었습니다.

<u>실제 결과</u>:

예약된 업데이트를 저장할 때 다음 오류가 발생합니다. *요청한 제품이 없습니다. 제품을 확인하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
