---
title: 'ACSD-59036: 하한과 상한이 모두 $0로 설정된 제품 가격을 로드할 때 예외가 발생합니다.'
description: ACSD-59036 패치를 적용하여 하한과 상한이 모두 *$0*으로 설정된 제품 가격을 로드할 때 예외가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
source-git-commit: d711fb8ff8876a4a514daade6d7df4d7cf7e3593
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# ACSD-59036: 하한과 상한이 모두 *$0*(으)로 설정된 제품 가격을 로드할 때 예외가 발생합니다.

ACSD-59036 패치는 하한과 상한이 모두 *$0*(으)로 설정된 제품 가격을 로드할 때 예외가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-59036입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

하한과 상한이 모두 *$0*(으)로 설정된 제품 가격을 로드할 때 예외가 발생합니다.

가격 범위가 있는 쿼리를 로드할 때 알고리즘이 NULL 값을 계산하지 않으므로 문제가 발생합니다. 이 문제를 해결하려면 하위 범위와 상위 범위가 모두 NULL인지 확인하고, NULL이면 두 제한에 대해 *0* 값을 할당할 수 있습니다. 이렇게 하면 오류가 발생하지 않습니다.

<u>재현 단계</u>:

1. *13* 간단한 제품을 만듭니다.
1. 모든 *13* 제품을 범주에 할당합니다.
1. 한 제품의 가격을 *$1322.94*(으)로 설정합니다.
1. 다른 모든 제품의 가격을 *$0*(으)로 설정합니다.
1. [!DNL OpenSearch]을(를) 검색 엔진으로 구성합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**(으)로 이동하여 **[!UICONTROL PLP]** 카운트를 *16*(으)로 설정합니다.
1. **[!UICONTROL Price Navigation Step Calculation]**&#x200B;을(를) *자동(제품 개수 균등화)*(으)로 설정합니다.
1. 전체 색인 재지정을 실행합니다.
1. *[!UICONTROL Category]* 페이지를 엽니다.

<u>예상 결과</u>:

*[!UICONTROL Category]* 페이지에 모든 제품이 표시됩니다.

<u>실제 결과</u>:

오류 발생:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
