---
title: 'ACSD-48210: 저장소 보기 특정 범위 특성이 전역 값을 재정의합니다.'
description: ACSD-48210 패치를 적용하여 특정 저장소 보기에서 *[!UICONTROL Website Scope]* 특성을 업데이트하는 Adobe Commerce 문제가 전역 범위의 특성 값을 재정의합니다.
feature: Products, Attributes
role: Admin, Developer
source-git-commit: 0fb14710d126aa4b4d6f5b6d0c70b190dcae81ae
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-48210: 저장소 보기 특정 범위 특성이 전역 값을 재정의합니다.

ACSD-48210 패치는 특정 저장소 보기 내에서 *[!UICONTROL Website Scope]* 특성을 업데이트할 때 전역 범위의 특성 값을 재정의하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48210입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 저장소 보기 내에서 *[!UICONTROL Website Scope]* 특성을 업데이트할 때 전역 범위의 특성 값을 재정의합니다.

동일한 `SKU` 및 `store_view_code`을(를) 공유하는 여러 행으로 제품 가격을 가져오면 *[!UICONTROL All Store View]* 및 *[!UICONTROL Default Store]* 범위의 가격이 잘못 업데이트되었습니다. 특정 스토어 보기에서 웹 사이트 범위 속성을 수정해도 더 이상 전역 범위에 있는 속성 값이 재정의되지 않습니다.
<u>재현 단계</u>:

1. *[!UICONTROL Catalog Price Scope]*&#x200B;을(를) *[!UICONTROL Website]*(으)로 구성합니다.
1. 이름이 *SP01*&#x200B;인 간단한 제품을 만들고 가격을 *$84.50*(으)로 설정합니다.
1. 아래에 제공된 다음 CSV를 사용하여 제품을 가져옵니다.

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. *[!UICONTROL All Store View]* 및 *[!UICONTROL Default Store]* 범위에서 제품 가격을 확인하십시오.

<u>예상 결과</u>:

* *[!UICONTROL Default Store]* 범위에는 비어 있지 않은 첫 번째 값이 사용됩니다.
* *[!UICONTROL All Store View]* 범위는 변경되지 않습니다.

<u>실제 결과</u>:

* *[!UICONTROL All Store View]* 범위 가격이 *$86.59*(으)로 변경됩니다.
* *[!UICONTROL Default Store]* 범위 가격이 *$86.59*(으)로 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
