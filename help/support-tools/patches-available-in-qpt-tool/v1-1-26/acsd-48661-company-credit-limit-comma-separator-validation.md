---
title: 'ACSD-48661: 회사 크레딧 제한 쉼표 구분 기호 유효성 검사 문제'
description: ACSD-48661 패치를 적용하여 회사 크레딧 제한이 999보다 큰 경우 쉼표 구분 기호로 인해 유효성 검사 오류로 인해 회사가 저장되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: 회사 크레딧 제한 쉼표 구분 기호 유효성 검사 문제

ACSD-48661 패치는 회사 크레딧 제한이 999보다 큰 경우 쉼표 구분 기호로 인해 유효성 검사 오류로 인해 회사가 저장되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48661입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사 신용 한도가 999보다 큰 경우 쉼표 구분 기호는 검증 오류로 인해 회사가 저장되지 않도록 합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;에서 회사 기능을 사용하도록 설정하십시오.
1. 회사를 만들고 **[!UICONTROL Company Credit]** 탭에서 999보다 큰 크레딧 제한을 추가하십시오.
1. 회사를 구하십시오.
1. 회사를 편집하고 다시 저장해 보십시오.

<u>예상 결과</u>:

당신은 신용 한도를 정하지 않고도 회사를 살릴 수 있다. 금액 및 가격에 대한 입력 필드에 쉼표가 지원되지 않습니다.

<u>실제 결과</u>:

*[!UICONTROL Credit Limit]* 필드의 유효성 검사 오류로 인해 회사를 저장할 수 없습니다. [!UICONTROL Credit Limit] 필드에 쉼표가 허용되지 않는 경우에도 Adobe Commerce은 크레딧 제한에 쉼표 구분 기호를 자동으로 추가합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
