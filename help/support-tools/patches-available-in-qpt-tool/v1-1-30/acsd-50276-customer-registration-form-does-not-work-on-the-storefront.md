---
title: "ACSD-50276: 다중 선택 고객 특성이 생성된 경우 고객 등록 양식이 상점 첫 화면에서 작동하지 않음"
description: ACSD-50276 패치를 적용하여 다중 선택 고객 속성이 생성된 경우 고객 등록 양식이 상점 첫 화면에서 작동하지 않는 Adobe Commerce 문제를 수정합니다.
exl-id: 542eb93a-3719-4e2d-bb1b-87817f0812b4
feature: Attributes, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-50276: 다중 선택 고객 특성이 생성된 경우 고객 등록 양식이 상점 첫 화면에서 작동하지 않습니다.

ACSD-50276 패치는 다중 선택 고객 특성이 생성될 때 고객 등록 양식이 상점 첫 화면에서 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-50276입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다중 선택 고객 특성이 만들어지는 경우 고객 등록 양식이 상점 첫 화면에서 작동하지 않습니다.

<u>재현 단계</u>:

1. 다음 설정으로 다중 선택 고객 속성을 새로 만듭니다.

   * *[!UICONTROL Required = Yes]*
   * *[!UICONTROL Show on storefront = Yes]*, *[!UICONTROL Customer registration form]*&#x200B;을(를) 선택하십시오.

1. 상점에서 고객 등록 양식을 엽니다.

<u>예상 결과</u>:

고객 등록 양식이 정상적으로 로드되었습니다.

<u>실제 결과</u>:

* 고객 등록 양식이 로드되지 않습니다.
* 다음 오류가 기록됩니다.

  ```PHP
  report. CRITICAL: Exception: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in vendor/magento/module-custom-attribute-management/Block/Form/Renderer/Multiselect.php
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
