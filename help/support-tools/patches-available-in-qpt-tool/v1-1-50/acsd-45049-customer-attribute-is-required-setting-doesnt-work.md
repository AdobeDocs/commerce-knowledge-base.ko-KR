---
title: "ACSD-45049: 관리자의 웹 사이트 범위에 따라 고객 '필수' 속성 설정이 작동하지 않음"
description: ACSD-45049 패치를 적용하여 Admin의 웹 사이트 범위에 따라 고객 "[!UICONTROL Is required]" 특성이 제대로 재정의되지 않은 Adobe Commerce 문제를 해결합니다.
feature: Attributes, Customers
role: Admin, Developer
source-git-commit: 16e7c9e4e4bbbc62db0671016bce85ecb6414622
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-45049: 고객 *[!UICONTROL Is required]* 특성 설정이 관리자의 웹 사이트 범위에 따라 작동하지 않습니다.

ACSD-45049 패치는 관리자의 웹 사이트 범위에 따라 고객 *[!UICONTROL Is required]* 특성 설정이 제대로 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45049입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p7 및 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Admin의 웹 사이트 범위에 따라 고객 *[!UICONTROL Is required]* 특성 설정이 제대로 작동하지 않습니다.

<u>재현 단계</u>:

1. 두 개의 웹 사이트를 만듭니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**&#x200B;을(를) 엽니다.
1. 새 특성을 만드십시오. **[!UICONTROL Is value required]** = *아니요*&#x200B;를 설정하십시오.
1. 기본 웹 사이트로 전환하고 **[!UICONTROL Is value required]** = *예*&#x200B;를 변경합니다. 다른 웹 사이트에는 기본값이 있습니다.
1. 기본이 아닌 웹 사이트에 대해 관리자로부터 새 고객을 만듭니다.

<u>예상 결과</u>:

기본 웹 사이트가 아닌 웹 사이트에는 속성이 필요하지 않습니다.

<u>실제 결과</u>:

* Admin에서 고객을 만들 때 기본값이 아닌 웹 사이트에 속성이 필요합니다.
* storefront에서 고객을 등록할 때 기본값이 아닌 웹 사이트에는 속성이 필요하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
