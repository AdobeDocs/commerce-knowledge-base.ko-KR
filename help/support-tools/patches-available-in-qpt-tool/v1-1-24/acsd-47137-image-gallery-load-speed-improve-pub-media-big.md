---
title: '''ACSD-47137: 이미지 갤러리 로드 속도 개선 ''pub/media'' 폴더 큰'''
description: ACSD-47137 패치를 적용하면 'pub/media' 폴더가 매우 클 때 이미지 갤러리의 로드 속도를 향상시킬 수 있습니다.
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137: `pub/media` 폴더가 클 때 이미지 갤러리 로드 속도를 개선합니다.

ACSD-47137 패치는 `pub/media` 폴더가 매우 클 때 이미지 갤러리의 로드 속도를 향상시킵니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47137입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`pub/media` 폴더가 매우 큰 경우 이미지 갤러리의 로드 속도가 느립니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자 > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]**(으)로 이동하여 _아니요_&#x200B;로 이동합니다.
1. 구성 캐시를 정리합니다.
1. 로그아웃한 후 관리자로 다시 로그인합니다.
1. 관리 사이드바에서 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**(으)로 이동하여 루트 범주를 선택합니다.
1. **[!UICONTROL Content]** 섹션을 확장하고 **[!UICONTROL Select from Gallery]**&#x200B;을(를) 클릭합니다.

페이지를 로드할 때 Adobe Commerce에서 `media_gallery/directories/gettree` 요청을 보내 미디어 폴더 트리를 로드합니다.

<u>예상 결과</u>:

`media_gallery/directories/gettree` 요청은 `pub/media/` 폴더의 전체 경로 목록을 반복하는 것 외에 필요한 디렉터리에서만 콘텐츠를 로드해야 합니다.

<u>실제 결과</u>:

`pub/media/` 폴더에 많은 콘텐츠가 있는 경우 `media_gallery/directories/gettree` 요청을 로드하는 데 시간이 오래 걸립니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
