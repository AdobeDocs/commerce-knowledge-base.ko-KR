---
title: 'ACSD-58790:  [!DNL Chrome]의 모바일 보기에서 제품 세부 사항 페이지 이미지의 핀치-투-줌 기능을 수정합니다'
description: ACSD-58790은  [!DNL Chrome] 의 모바일 보기의 이미지가 예상대로 확대되지 않았던 Adobe Commerce 문제를 해결했습니다.
feature: Storefront
role: Admin, Developer
source-git-commit: 51c740dc70937c7b80d8492d02ee4a758f103a35
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-58790: [!DNL Chrome]의 모바일 보기에서 제품 세부 사항 페이지 이미지의 핀치-투-줌 기능을 수정합니다.

ACSD-58790 패치는 [!DNL Chrome]의 모바일 보기에서 이미지가 예상대로 확대되지 않았던 Adobe Commerce 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58790입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Chrome]의 모바일 보기에서 제품 세부 사항 페이지 이미지의 핀치-투-줌 기능을 수정합니다.

<u>재현 단계</u>:

1. 이미지를 사용하여 제품을 만듭니다.
1. [!DNL Chrome] 브라우저에서 제품을 엽니다.
1. 이미지를 클릭하고 이미지가 두 번 클릭으로 확대되는지 확인합니다.
1. [!DNL Chrome] 개발자 도구를 사용하여 모바일 보기로 전환합니다.
1. 이미지를 클릭합니다.
1. 두 번 탭합니다.

<u>예상 결과</u>:

이미지를 두 번 클릭하면 확대됩니다.

<u>실제 결과</u>:

두 번 클릭해도 이미지가 확대되지 않습니다. 확대/축소 기능이 [!DNL Firefox]에서 예상대로 작동하므로 이 문제는 모바일 보기의 [!DNL Chrome]에만 해당됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
