---
title: 'ACSD-59229: 오래된 X-Magento-Vary 값으로 인해 고객 그룹의 데이터 잘못 할당'
description: ACSD-59229 패치를 적용하여 요청의 오래된 X-Magento-Vary 값으로 인해 고객 그룹 관련 정보가 잘못된 세그먼트에 저장되는 Adobe Commerce 문제를 수정합니다.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: 090b674a-5103-48cd-9426-41166bf9272c
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-59229: 오래된 X-Magento-Vary 값으로 인해 고객 그룹의 데이터 잘못 할당

ACSD-59229 패치는 요청의 오래된 X-Magento-Vary 값으로 인해 고객 그룹 관련 정보가 잘못된 세그먼트에 저장되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-59229입니다. 이 문제는 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

요청의 오래된 X-Magento-Vary 값으로 인해 고객 그룹 관련 정보가 잘못된 세그먼트에 저장됩니다.

<u>필수 구성 요소</u>:

샘플 데이터가 있는 Adobe Commerce B2B가 설치되어 있고 [!DNL Varnish]이(가) 구성되어 있는지 확인하십시오.

<u>재현 단계</u>:

1. [!DNL SKU 24-MB01]에 대한 고급 가격 설정:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *도매* = *$200*
      * *판매업체* = *$30*

1. 두 개의 고객 계정을 만듭니다.
1. 두 고객을 **도매** 그룹에 할당하십시오.
1. 두 개의 서로 다른 브라우저 세션을 열고 각 고객에게 로그인합니다.
1. 각 고객의 **[!UICONTROL 24-MB01]** 제품 페이지로 이동하여 표시되는 가격이 *$200*&#x200B;인지 확인하십시오.
1. 고객 중 하나의 고객 그룹을 **소매**(으)로 변경합니다.
1. `bin/magento cache:flush full_page` 명령을 사용하여 캐시를 지웁니다.
1. 각 고객의 제품 페이지를 새로 고칩니다.

<u>예상 결과</u>:

1. 소매 고객은 제품에 대한 올바른 가격인 *$30*&#x200B;을(를) 볼 수 있습니다.
1. 도매 고객은 제품에 대한 올바른 가격인 *$200*&#x200B;을(를) 볼 수 있습니다.

<u>실제 결과</u>:

1. 소매 고객은 제품에 대한 올바른 가격인 *$30*&#x200B;을(를) 볼 수 있습니다.
1. 도매 고객에게 제품에 대한 *$30*(소매 가격)의 잘못된 가격이 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
