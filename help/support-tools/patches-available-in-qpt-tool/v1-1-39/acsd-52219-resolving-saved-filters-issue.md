---
title: 'ACSD-52219: 책갈피 보기 전환에서 관리 그리드 필터 문제 해결'
description: ACSD-52219 패치를 적용하여 책갈피 보기 사이를 자주 전환할 때 관리 그리드의 저장된 필터가 예상대로 작동하지 않는 Adobe Commerce 문제를 수정합니다.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: 책갈피 보기 전환에서 관리 그리드 필터 문제 해결

ACSD-52219 패치는 책갈피 보기 사이를 자주 전환할 때 관리 그리드의 저장된 필터가 예상대로 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52219입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

책갈피 보기 사이를 자주 전환하는 경우 관리 그리드에 저장된 필터가 의도한 대로 작동하지 않습니다.

<u>재현 단계</u>:

1. 관리자의 [!DNL Sales Order] 그리드에 액세스합니다.
1. 2~3개의 필터를 만듭니다.
1. 보기를 전환하여 필터 설정을 확인하여 정확하게 저장되었는지 확인합니다.
1. Filter1 또는 Filter2로 이동합니다.
1. 페이지를 새로 고쳐 표시된 데이터를 업데이트합니다.
1. 다른 보기로 전환하고 필터가 변경되지 않은 것을 확인합니다.
1. 특정 필터가 설정되지 않았더라도 기본 보기에 필터링된 결과가 표시됩니다.

<u>예상 결과</u>:

필터는 서로 변경되지 않고 원래 상태를 유지합니다.

<u>실제 결과</u>:

보기를 수정할 때 필터가 혼합되고 올바른 보기가 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
