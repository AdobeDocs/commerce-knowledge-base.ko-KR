---
title: 'ACSD-54983: 비활성 사용자는 GraphQL을 사용하는 회사 사용자 UID를 사용할 수 없음'
description: ACSD-54983 패치를 적용하여 사용자 상태가 비활성으로 설정된 경우 Adobe Commerce 요청으로 회사 사용자 UID를 가져올 수 없는 GraphQL 문제를 해결합니다.
feature: GraphQL
role: Admin, Developer
exl-id: 57e7b9ca-3421-4b50-86b4-abdf1b3d79d1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983: 비활성 사용자는 GraphQL을 사용하는 회사 사용자 UID를 사용할 수 없습니다

ACSD-54983 패치는 사용자 상태가 비활성으로 설정된 경우 GraphQL 요청으로 회사 사용자 UID를 가져올 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54983입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 상태가 비활성으로 설정된 경우 GraphQL 요청으로 회사 사용자 UID를 가져올 수 없습니다.

<u>재현 단계</u>:

1. 관리자 권한으로 회사를 만듭니다. 예: company@test.com.
1. 새 고객을 만듭니다.
1. 새 고객을 회사에 지정합니다.
1. **[!UICONTROL company admin token]**&#x200B;을(를) 가져옵니다.
1. **[!UICONTROL company admin token]**&#x200B;을(를) 사용하여 회사 구조를 가져옵니다. 개발자 설명서에서 [회사 구조 반환](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure)을 참조하십시오.
1. 응답에는 해당 ID를 가진 *ACTIVE* 고객만 포함됩니다.
1. 회사 사용자를 *비활성*(으)로 업데이트하십시오.
1. 회사 구조를 다시 가져오십시오.

<u>예상 결과</u>:

상태가 비활성으로 설정되면 회사 사용자 UID를 가져올 수 있습니다.

<u>실제 결과</u>:

비활성 고객이 목록에 없습니다. 상태가 비활성으로 설정된 경우 회사 사용자 UID를 가져올 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
