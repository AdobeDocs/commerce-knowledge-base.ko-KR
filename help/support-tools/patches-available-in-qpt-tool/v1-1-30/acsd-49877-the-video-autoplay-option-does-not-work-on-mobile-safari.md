---
title: 'ACSD-49877: 모바일 [!DNL Safari]에서 비디오 자동 재생이 작동하지 않습니다.'
description: ACSD-49877 패치를 적용하여 비디오가 원격 비디오 파일에 직접 연결되어 있는 경우  [!DNL Safari] 모바일에서 비디오 자동 재생 옵션이 작동하지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: 모바일 [!DNL Safari]에서 비디오 자동 재생이 작동하지 않습니다.

ACSD-49877은 비디오가 원격 비디오 파일에 직접 연결되어 있을 때 모바일 [!DNL Safari]의 자동 재생 옵션이 작동하지 않는 문제를 해결했습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49877입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 [!magento/quality-patches] 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]: 패치 검색]에서 호환성을 확인하십시오. 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

비디오가 스트리밍 서비스가 아닌 원격 비디오 파일에 직접 연결되어 있는 경우 모바일 [!DNL Safari]에서 비디오 자동 재생이 작동하지 않습니다.

<u>필수 구성 요소</u>:
[!DNL Page Builder] 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 새 CMS 페이지를 만들고 [!DNL Page Builder](으)로 **[!UICONTROL Content Value]**&#x200B;을(를) 편집합니다.
1. 콘텐츠에 *Tab* 요소를 추가하고 *Tab* 내에 *비디오 요소*&#x200B;를 추가합니다.
1. 이제 톱니바퀴 단추를 클릭하여 *비디오 요소*&#x200B;를 편집합니다.
1. mp4 비디오 파일에 대한 링크를 [!UICONTROL Video URL] 필드에 추가합니다.
1. **[!UICONTROL Autoplay]** 필드를 *예*(으)로 표시합니다.
1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.
1. iPhone을 사용하여 [!DNL Safari]에서 최근에 만든 페이지를 엽니다.

<u>예상 결과</u>

자동 재생 옵션은 iPhone을 사용하여 [!DNL Safari]에서 작동합니다.

<u>실제 결과</u>

iPhone을 사용하는 [!DNL Safari]에서는 자동 재생 옵션이 작동하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
