---
title: 'ACSD-55305: [!UICONTROL My Account]에서 회사 사용자를 편집하는 동안 팝업이 중지됨'
description: ACSD-55305 패치를 적용하여 [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] 페이지의 [!UICONTROL Edit Company User] 팝업이 화면에서 로더로 멈추는 Adobe Commerce 문제를 해결합니다.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: [!UICONTROL My Account]에서 회사 사용자를 편집하는 동안 팝업이 고정됨

ACSD-55305 패치는 [!UICONTROL My Account]> [!UICONTROL Company Structure] 페이지의 [!UICONTROL Edit Company User] 팝업이 화면에 로더가 있는 상태로 멈추는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-55305입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* 페이지에서 *[!UICONTROL Edit Company User]* 팝업을 사용하려고 하면 화면에 로더가 표시된 상태로 고정되므로 오류가 발생합니다.

<u>재현 단계</u>:

1. B2B 회사를 만듭니다.
1. 고객을 위한 다중 선택 속성을 만듭니다.
1. 회사 관리자의 새로 만든 속성에 값을 할당합니다.
1. 회사 관리자로 로그인합니다.
1. [!UICONTROL account dashboard](으)로 이동하여 **[!UICONTROL Company Structure]**(으)로 이동합니다.
1. 사용자를 선택합니다.
1. **[!UICONTROL Edit Selected]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

양식 팝업이 정확하게 표시되어 회사 정보를 편집할 수 있는 옵션을 제공합니다.

<u>실제 결과</u>:

양식 팝업은 편집할 수 없는 상태로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
