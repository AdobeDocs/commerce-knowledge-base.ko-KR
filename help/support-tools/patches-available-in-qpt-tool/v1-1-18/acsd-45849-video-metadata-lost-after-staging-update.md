---
title: 'ACSD-45849: 스테이징 업데이트 후 비디오 메타데이터가 손실됨'
description: ACSD-45849 패치는 스테이징 업데이트가 적용된 후 비디오 메타데이터가 손실되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45849입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.
exl-id: 071a535d-f96c-4731-a17c-0b7bf8a87372
feature: Staging, Page Content
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-45849: 스테이징 업데이트 후 비디오 메타데이터가 손실됨

ACSD-45849 패치는 스테이징 업데이트가 적용된 후 비디오 메타데이터가 손실되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45849입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스테이징 업데이트가 적용된 후 비디오 메타데이터가 손실됩니다.

<u>재현 단계</u>:

1. **관리자** > **스토어** > **구성** > **카탈로그** > **제품 비디오**&#x200B;에서 YouTube API 키를 설정합니다.
1. YouTube 비디오를 사용하여 제품을 만듭니다. URL, 제목 및 설명이 채워집니다.
1. *이미지 및 비디오* 섹션을 변경하지 않고 매개 변수를 사용하여 제품에 대해 예약된 업데이트를 새로 만드십시오.
1. 예약된 변경 내용에서 **보기/편집**&#x200B;을 클릭합니다.
1. **이미지 및 비디오**(으)로 이동한 다음 비디오를 클릭합니다.

<u>예상 결과</u>:

URL, 제목 및 설명에 적절한 데이터가 포함되어 있습니다.

<u>실제 결과</u>:

URL, 제목 및 설명 필드가 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
