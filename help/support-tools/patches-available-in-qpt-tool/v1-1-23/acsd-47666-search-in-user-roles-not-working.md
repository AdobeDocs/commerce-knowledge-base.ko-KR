---
title: 'ACSD-47666: [!UICONTROL User Roles]에서 검색이 작동하지 않음'
description: ACSD-47666 패치를 적용하여 [!UICONTROL User Roles]의 필터 기능이 예상대로 작동하지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: c1b6d3ab-e132-4b09-8692-2b82f9ca6864
feature: Roles/Permissions, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-47666: **[!UICONTROL User Roles]**&#x200B;에서 검색이 작동하지 않음

ACSD-47666 패치는 **[!UICONTROL User Roles]**&#x200B;에서 검색이 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47666입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL User Roles]**&#x200B;의 필터 함수가 예상대로 작동하지 않습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자 > **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**&#x200B;에 로그인합니다.
1. 목록에서 기존 역할을 엽니다.
1. **[!UICONTROL Role Users]** 탭을 엽니다.
1. 열에 쿼리를 입력합니다.
1. Enter 키를 누릅니다.

<u>예상 결과</u>:

**[!UICONTROL User Roles]** 필터 함수는 쿼리를 기반으로 결과를 필터링해야 합니다.

<u>실제 결과</u>:

콘솔 오류 _(인덱스):9 발견되지 않은 TypeError로 무한 로드: null의 속성을 읽을 수 없습니다(&#39;down&#39; 읽기)_.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches). 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
