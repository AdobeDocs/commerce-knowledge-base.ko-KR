---
title: 'ACSD-48807: 제품 검토가 스토어뷰로 필터링되지 않음'
description: ACSD-48807 패치를 적용하여 제품 검토가 GraphQL을 통해 상점 보기로 필터링되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 754ef455-ff06-4832-9eb6-ad8cccec8799
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48807: 제품 리뷰가 스토어뷰로 필터링되지 않음

ACSD-48807 패치는 제품 검토가 GraphQL을 통해 상점 보기를 통해 필터링되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48807입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 리뷰는 GraphQL을 통해 스토어로 필터링되지 않습니다.

<u>재현 단계</u>:

1. 추가 스토리를 만듭니다.
1. 고객 계정을 만들고 로그인합니다.
1. 기본 스토어에서 제품에 대한 검토를 생성합니다.
1. 다른 스토뷰로 전환하고 제품에 대한 다른 검토를 만듭니다.
1. Adobe Commerce 관리에서 두 리뷰를 모두 승인합니다.
1. 헤더의 1단계에서 생성된 상점 보기를 지정하면서 제품 검토를 검색하도록 고객 GraphQL 쿼리를 보냅니다.
1. 응답을 확인합니다.

<u>예상 결과</u>:

지정된 스토어에 대한 제품 검토만 응답에서 반환됩니다.

<u>실제 결과</u>:

두 리뷰가 응답에서 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
