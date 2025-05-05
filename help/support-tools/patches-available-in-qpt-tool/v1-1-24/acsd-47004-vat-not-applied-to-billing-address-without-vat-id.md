---
title: 'ACSD-47004: VAT ID가 없는 청구 주소에 VAT가 적용되지 않음'
description: ACSD-47004 패치를 적용하여 VAT ID가 없는 청구 주소에 VAT가 적용되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 04706219-be1d-4d9a-a8bf-f5c24b45076d
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004: VAT ID가 없는 청구 주소에 VAT가 적용되지 않음

ACSD-47004 패치는 VAT ID가 없는 청구 주소에 VAT가 적용되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47004입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

VAT ID가 없는 청구 주소에는 VAT가 적용되지 않습니다.

<u>재현 단계</u>:

1. [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]**&#x200B;을(를) 열고 **[!UICONTROL Enable Automatic Assignment to Customer Group]**&#x200B;을(를) *[!UICONTROL Yes]*(으)로 설정합니다.
1. VAT ID 유효성 검사에 대해 다른 그룹을 설정합니다. For example:
   ![VAT-ID 유효성 검사](/help/support-tools/patches-available-in-qpt-tool/assets/vat-id-validations.png)
1. 새 고객을 등록합니다.
1. VAT 없이 새 기본 주소를 추가합니다. For example:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. 고객의 그룹이 [!UICONTROL General] (으)로 남아 있는지 확인합니다.
1. 이 주소를 편집하고 유효한 VAT 번호를 추가하십시오.

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. 고객의 그룹이 [!UICONTROL Retailer] (으)로 변경되었는지 확인하십시오.
1. 주소를 편집하고 VAT 번호를 제거합니다.

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>예상 결과</u>:

고객 그룹이 기본 [!UICONTROL General] 그룹으로 자동 변경되었습니다.

<u>실제 결과</u>:

고객 그룹은 자동으로 기본 [!UICONTROL General] 그룹으로 변경되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
