---
title: 'MDVA-38308: 비활성화된 제품에 Vimeo 비디오를 추가한 후 오류 발생'
description: '''Adobe Commerce용 MDVA-38308 품질 패치는 사용자가 사용할 수 없는 제품에 Vimeo 비디오를 추가할 때 다음과 같은 오류 메시지를 받는 문제를 해결합니다. *알림: 색인이 정의되지 않음: 806행의 /lib/internal/Magento/Framework/File/Uploader.php 확장*. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38308입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정될 예정입니다."'
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308: 비활성화된 제품에 Vimeo 비디오를 추가한 후 오류 발생

Adobe Commerce용 MDVA-38308 품질 패치는 사용자가 비활성화된 제품에 Vimeo 비디오를 추가할 때 다음과 같은 오류 메시지를 받는 문제를 해결합니다. *알림: 색인이 정의되지 않음: 확장명: /lib/internal/Magento/Framework/File/Uploader.php행 806,*. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38308입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.4.1-p1, 2.4.2-p1

**Adobe Commerce 버전과 호환:**
Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

비활성화된 제품에 Vimeo 비디오를 추가하면 다음 오류 메시지가 표시됩니다. *알림: 색인이 정의되지 않음: 확장명이 /lib/internal/Magento/Framework/File/Uploader.php줄 806*

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 생성된 제품을 비활성화합니다.
1. 비활성화된 제품에 Vimeo 비디오를 추가해 보십시오.

<u>예상 결과</u>:

비디오가 오류 없이 추가됩니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.
*알림: 색인이 정의되지 않았습니다. 확장명이 /lib/internal/Magento/Framework/File/Uploader.php입니다. 줄 806*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html)

## 관련 읽기

지원 기술 자료의 품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 지원 기술 자료에서 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
