---
title: 'ACSD-49628: [!DNL Page Builder] CORS 오류로 인해 제품을 저장할 수 없음'
description: ACSD-49628 패치를 적용하여  [!DNL Page Builder] CORS 오류로 인해 제품 저장이 되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: c6e2f0b3-aea0-4caf-8b69-9644b38c909c
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder]개의 CORS 오류로 인해 제품을 저장할 수 없습니다.

ACSD-49628 패치는 [!DNL Page Builder]개의 CORS 오류로 인해 관리자가 제품을 저장할 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49628입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Page Builder]개의 CORS 오류로 인해 제품을 저장할 수 없습니다.

<u>재현 단계</u>:

1. 관리자로 로그인합니다.
1. 다음 권한을 사용하여 사용자 역할을 만듭니다.

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. *[!UICONTROL Content]* 권한을 추가하지 마십시오.
1. 다른 관리 사용자를 만들고 위에서 만든 역할을 이 사용자에게 할당합니다.
1. 제품을 만들고 로그아웃합니다.
1. 두 번째 관리자로 로그인합니다.
1. 제품을 편집하고 저장해 보십시오.

<u>예상 결과</u>:

두 번째 관리자가 제품을 저장할 수 있지만 *[!UICONTROL Content]* 권한 없이 관리자에게 **[!UICONTROL Edit with Page Builder]** 단추가 표시되지 않습니다.

<u>실제 결과</u>:

두 번째 관리자가 여러 개의 [!DNL Page Builder] 오류로 인해 제품을 저장할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
