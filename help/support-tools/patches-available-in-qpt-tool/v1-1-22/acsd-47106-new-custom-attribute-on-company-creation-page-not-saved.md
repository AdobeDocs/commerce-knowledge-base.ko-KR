---
title: "ACSD-47106: 회사 만들기 페이지의 새 사용자 지정 특성이 저장되지 않음"
description: ACSD-47106 패치를 적용하여 회사 생성 페이지의 새 사용자 지정 속성에 값을 저장할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106: 회사 만들기 페이지의 새 사용자 지정 특성이 저장되지 않음

ACSD-47106 패치는 회사 만들기 페이지의 새 사용자 지정 특성에 값을 저장할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47106입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사 만들기 페이지의 새 사용자 지정 특성에 값을 저장할 수 없습니다.

<u>필수 구성 요소</u>:

* B2B 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. Commerce 관리자 > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**(으)로 이동합니다.
1. 새 특성을 만듭니다. _테스트 01_.
1. Commerce 관리자 > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** >(으)로 이동하여 필요한 모든 세부 정보를 사용하여 새 회사를 만드십시오.
1. 사용자 지정 특성 _테스트 01_&#x200B;에 값을 추가해 보십시오.
1. 사용자 지정 특성 _테스트 01_&#x200B;의 값을 업데이트해 보십시오.

<u>예상 결과</u>:

변경 사항이 저장됩니다.

<u>실제 결과</u>:

변경 사항이 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
