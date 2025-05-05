---
title: 'ACSD-48866: 범주에 대한 RSS 피드를 요청할 때 오류 발생'
description: ACSD-48866 패치를 적용하여 카테고리에 대한 RSS 피드를 요청할 때 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
exl-id: 0b509f32-3904-47c3-aacd-df8b6adbf443
feature: Admin Workspace, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-48866: 범주에 대한 RSS 피드를 요청할 때 오류 발생

ACSD-48866 패치는 범주에 대한 RSS 피드를 요청할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48866입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

범주에 대한 RSS 피드를 요청할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL RSS Config]** > **[!UICONTROL Enable RSS]**&#x200B;에서 RSS 피드를 활성화합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL Catalog]** > **[!UICONTROL Top Level Category]**&#x200B;에서 [!UICONTROL Top Level Category]을(를) 활성화합니다.
1. 상점 첫 화면 RSS 피드 범주 페이지를 찾아봅니다.
1. `var/log`에서 로그 파일을 확인하십시오.

<u>예상 결과</u>:

로그 파일에 오류가 없습니다.

<u>실제 결과</u>:

로그 파일에 다음 오류가 표시됩니다.

```
Text fields are not optimised for operations that require per-document field data like aggregations and sorting, so these operations are disabled by default. Please use a keyword field instead. Alternatively, set fielddata=true on [updated_at] in order to load field data by uninverting the inverted index.
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
