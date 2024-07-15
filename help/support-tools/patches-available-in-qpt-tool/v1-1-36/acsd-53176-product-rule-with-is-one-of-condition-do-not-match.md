---
title: '''ACSD-53176: ''is one of'' 조건이 있는 제품 규칙이 일치하지 않음'''
description: ACSD-53176 패치를 적용하여 관련 제품 규칙 'is one of' 조건이 'Products to Match'에 대해 제대로 작동하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Marketing Tools
role: Admin
exl-id: 91f05f5b-6a5e-4b93-9dfb-88cbeccb6c9e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-53176: `is one of` 조건을 사용하는 제품 규칙이 일치하지 않습니다.

ACSD-53176 패치는 **Products가 일치**&#x200B;하는 데 관련 제품 규칙 `is one of` 조건이 올바르게 작동하지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53176입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관련 제품 규칙 `is one of` 조건이 **Products를 일치**&#x200B;하는 데 올바르게 작동하지 않습니다.

<u>재현 단계</u>:

1. 3~4개의 제품을 만듭니다.
1. 새 관련 제품 규칙을 만듭니다.

   둘 이상의 제품과 일치하도록 규칙을 설정합니다.
   * `SKU is one of "S1,S2".`

   두 개 이상의 항목을 표시하는 규칙을 설정합니다.
   * `Product SKU is one of constant value "S2,S3".`

1. 상점에서 S1 제품을 엽니다.

<u>예상 결과</u>:

관련 제품 &quot;S2&quot;와 &quot;S3&quot;은 제품 페이지 &quot;S1&quot;과 &quot;S2&quot;에 모두 표시됩니다.

<u>실제 결과</u>:

관련 제품이 제품 페이지에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
