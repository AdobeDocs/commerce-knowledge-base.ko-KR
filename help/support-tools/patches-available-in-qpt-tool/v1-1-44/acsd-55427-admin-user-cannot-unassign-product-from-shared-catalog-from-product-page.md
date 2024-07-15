---
title: "ACSD-55427: 관리자가 제품 페이지의 **[!UICONTROL Product in Shared Catalogs]**에서 제품 할당을 취소할 수 없습니다."
description: ACSD-55427 패치를 적용하여 **[!UICONTROL Product in Shared Catalogs]**에서 제품 할당을 취소할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: 관리자가 제품 페이지의 **[!UICONTROL Product in Shared Catalogs]**&#x200B;에서 제품 할당을 취소할 수 없습니다.

ACSD-55427 패치는 Commerce 관리자의 카탈로그에 있는 제품 페이지에서 **[!UICONTROL Product in Shared Catalogs]**&#x200B;의 제품 할당을 취소할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-55427입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Commerce 관리자의 카탈로그에 있는 제품 페이지에서 **[!UICONTROL Product in Shared Catalogs]**&#x200B;의 제품 할당을 취소할 수 없습니다.

<u>재현 단계</u>:

필수 구성 요소: B2B와 **[!UICONTROL Shared Catalogs]**&#x200B;이(가) 모두 활성화된 Adobe Commerce이 설치되었습니다.
1. 제품을 만듭니다.
1. 공유 카탈로그 대시보드로 이동하여 기본 공유 카탈로그를 엽니다.
1. 제품을 기본 카탈로그에 지정하고 제품 가격보다 낮은 가격을 설정합니다.
1. 공유 카탈로그를 저장합니다.
1. [!UICONTROL CRON]을(를) 실행하여 소비자/인덱서를 업데이트합니다.
1. 제품을 열고 **[!UICONTROL Product in Shared Catalogs]** 섹션 아래에서 제품을 제거합니다.

<u>예상 결과</u>:

**[!UICONTROL Product in Shared Catalogs]** 섹션 아래에서 제품을 제거해야 합니다.

<u>실제 결과</u>:

제품이 **[!UICONTROL Product in Shared Catalogs]** 섹션에 계속 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
