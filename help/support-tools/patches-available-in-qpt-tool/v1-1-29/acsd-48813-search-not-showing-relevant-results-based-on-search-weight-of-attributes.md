---
title: 'ACSD-48813: 검색 시 속성의 검색 가중치에 따라 관련 결과가 표시되지 않음'
description: ACSD-48813 패치를 적용하여 속성의 검색 가중치에 따라 검색 결과가 표시되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 089e3ab3-0dfa-4f81-85c7-f6060f326d97
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813: 검색 시 속성의 검색 가중치에 따라 관련 결과가 표시되지 않음

ACSD-48813 패치는 특성의 검색 가중치에 따라 검색 결과가 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48813입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

검색 시 속성의 검색 가중치에 따라 관련 결과가 표시되지 않습니다.

<u>재현 단계</u>:

1. 샘플 데이터를 사용하여 Adobe Commerce을 설치합니다.
1. 검색 엔진을 [!DNL Elasticsearch](으)로 설정합니다.
1. 관리자로 로그인합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**(으)로 이동합니다.
1. *name* 특성을 엽니다.
1. 상점 첫 화면 *[!UICONTROL Properties]* 탭을 엽니다.
1. 드롭다운 값에서 [!UICONTROL Search Weight] = *10*&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Save Attribute]**&#x200B;을(를) 클릭합니다.
1. 이제 상점을 열고 *뒤로*&#x200B;라는 단어를 검색합니다.

<u>예상 결과</u>:

배낭 제품이 검색 결과 맨 위에 반환됩니다.

<u>실제 결과</u>:

배낭 제품이 검색 결과 중간에 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
