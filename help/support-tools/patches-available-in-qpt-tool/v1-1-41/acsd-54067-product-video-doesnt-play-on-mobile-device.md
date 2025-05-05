---
title: 'ACSD-54067: 모바일 장치에서 제품 비디오가 재생되지 않음'
description: ACSD-54067 패치를 적용하여 제품 비디오가 모바일 장치에서 재생되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Media, Products
role: Admin, Developer
exl-id: 369650ef-bcce-47c5-bbfe-39f3c2b1d73f
source-git-commit: 0795e3e0ba11002c8aff2794e16fa05f1c7e19c3
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-54067: 모바일 장치에서 제품 비디오가 재생되지 않음

ACSD-54067 패치는 모바일 장치에서 제품 비디오가 재생되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54067입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

모바일 장치에서 제품 비디오가 재생되지 않습니다.

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. 다음 명령을 실행합니다.
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. **[!UICONTROL Admin product list]** 페이지로 이동하여 *[!UICONTROL SKU product_dynamic_120]* 기준으로 필터링합니다.
1. 제품 페이지를 열고 **[!UICONTROL Images and Videos]** > 비디오 추가 > URL 입력(https://vimeo.com/347119375)으로 이동하여 저장합니다.
1. 상점으로 이동하여 *[!UICONTROL product_dynamic_120]*&#x200B;에 대한 제품 페이지를 엽니다.
1. 브라우저를 너비가 *320px*&#x200B;인 *모바일 장치*(으)로 설정하고 새로 고치십시오.
1. 갤러리 슬라이더에서 비디오를 선택하고 를 클릭하여 재생합니다.

<u>예상 결과</u>:

제품 비디오가 재생됩니다.

<u>실제 결과</u>:

제품 비디오가 재생되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
