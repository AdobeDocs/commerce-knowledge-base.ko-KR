---
title: 'ACSD-47179: 제한된 사용자 역할로 로그인하면 제품 리뷰의 대량 삭제가 작동하지 않음'
description: ACSD-47179 패치를 적용하여 제한된 사용자 역할로 로그인할 때 제품 리뷰의 대량 삭제가 작동하지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 85d7ce63-7dd6-4df4-b314-278d18e69fbb
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-47179: 제한된 사용자 역할로 로그인하는 경우 제품 리뷰의 대량 삭제가 작동하지 않음

ACSD-47179 패치는 제한된 사용자 역할로 로그인할 때 제품 리뷰의 대량 삭제가 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47179입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제한된 사용자 역할로 로그인하는 경우 제품 리뷰의 대량 삭제가 작동하지 않습니다.

<u>재현 단계</u>:

1. 보조 웹 사이트를 만듭니다.
1. 다음 섹션에 대한 전체 권한을 가진 보조 웹 사이트로 제한된 사용자 역할을 만듭니다.
   * 카탈로그
   * 고객
   * 마케팅
1. 제품을 만들고 보조 웹 사이트에 할당합니다.
1. 프론트엔드에서 제품에 대한 리뷰를 2개 추가합니다.
1. 방금 만든 제한된 관리자를 사용하여 [!DNL Commerce] 관리자에 로그인합니다.
1. 보류 중인 리뷰를 대량 삭제해 보십시오.

<u>예상 결과</u>:

충분한 권한이 있는 관리자는 보류 중인 검토를 대량 삭제할 수 있습니다.

<u>실제 결과</u>:

다음 오류가 발생했습니다. _문제가 발생했습니다. support_report.log_&#x200B;에서 예외가 발생했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
