---
title: 'ACSD-55238: 빈 제품 메타 설명 저장'
description: ACSD-55238 패치를 적용하여  [!DNL Page Builder] 이나 다른 HTML 편집기에서 생성된 HTML 코드가 포함된 제품 설명이 항상 메타 설명에 표시되는 Adobe Commerce 문제를 해결하십시오. 이를 비워 둘 방법은 없습니다.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: 빈 제품 메타 설명 저장

ACSD-55238 패치는 HTML 편집기에서 생성된 HTML 코드가 포함된 제품 설명이 항상 메타 설명에 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-55238입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Page Builder] 또는 다른 HTML 편집기에서 생성한 HTML 코드가 포함된 제품 설명은 항상 메타 설명에 표시되며 이를 비워 둘 방법은 없습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]**(으)로 이동하여 콘텐츠를 포함하는 새 블록을 만듭니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]**(으)로 이동하여 새 제품을 만드십시오. 메타 설명을 비어 있는 것으로 설정합니다.
1. *[!UICONTROL Content]* 탭에서 *[!DNL Page Builder]*&#x200B;을(를) 사용하여 위에서 만든 블록을 추가하고 제품을 저장합니다.
1. 상점 첫 화면에서 제품을 열고 문서 요소 `meta name = "description"`을(를) 확인합니다.

<u>예상 결과</u>:

메타 설명이 비어 있습니다.

<u>실제 결과</u>:

제품 설명에 블록이 있는 경우 제품 메타 설명에 사용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
