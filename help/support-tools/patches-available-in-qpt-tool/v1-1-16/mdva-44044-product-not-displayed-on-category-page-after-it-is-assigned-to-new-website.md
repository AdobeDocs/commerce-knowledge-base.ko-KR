---
title: 'MDVA-44044: 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않음'
description: MDVA-44044 패치는 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44044입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: e3a179ed-243c-4200-a01a-796657bd31ab
feature: Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-44044: 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않음

MDVA-44044 패치는 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44044입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 새 웹 사이트에 할당된 후에는 카테고리 페이지에 표시되지 않습니다.

<u>재현 단계</u>:

1. 인덱서 모드를 예약으로 설정합니다.
1. 보조 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. `index.php`에 보조 저장소 코드 추가:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. 새 카테고리를 만듭니다.
1. 새로 만든 카테고리에 할당된 새 제품을 만듭니다. 기본 웹 사이트에만 지정해야 합니다.
1. 크론을 작동시키세요
1. 상점 앞에서 범주를 엽니다.
1. 제품을 보조 웹 사이트에 할당합니다.
1. 크론을 다시 실행하세요.

<u>예상 결과</u>:

예약된 인덱서 다음에 제품이 카테고리 페이지에 표시됩니다.

<u>실제 결과</u>:

전체 색인 재지정이 될 때까지 해당 제품이 카테고리 페이지에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
