---
title: 'MDVA-39181: 관련 제품 규칙에 규칙에 정의되지 않은 범주의 제품이 표시됨'
description: MDVA-39181 패치는 관련 제품 규칙이 규칙에 정의되지 않은 범주의 제품을 표시하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39181입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: 관련 제품 규칙에 규칙에 정의되지 않은 범주의 제품이 표시됨

MDVA-39181 패치는 관련 제품 규칙이 규칙에 정의되지 않은 범주의 제품을 표시하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39181입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관련 제품 규칙은 규칙에 정의되지 않은 범주의 제품을 보여 줍니다.

<u>필수 구성 요소</u>:

샘플 데이터를 설치합니다.

<u>재현 단계</u>:

1. 특성 브랜드를 만들어 **Tops 특성 집합**&#x200B;에 추가합니다.
1. **Josie**, **Augusta** 및 **Ingrid** 재킷을 선택하여 **Women** > **Tops** > **Jackets 범주**&#x200B;에서 브랜드 키티에 추가합니다.
1. **Beaumont**, **Hyperion** 및 **Kenobi** 재킷을 선택하여 **Men** > **Tops** > **Jacket 범주**&#x200B;에서 브랜드 키티에 추가합니다.
1. 관련 제품 만들기:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * 일치하는 제품:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * 표시할 제품:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. 프론트엔드에서 SKU WJ04를 열고 관련 제품을 확인하십시오.
1. 이와 다른 경우 **여성** > **상단** > **재킷**&#x200B;에서 범주 ID를 업데이트하십시오.

<u>예상 결과</u>:

관련 제품에는 동일한 브랜드 및 동일한 하위 카테고리의 제품만 표시됩니다.

<u>실제 결과</u>:

관련 제품은 동일한 브랜드로 표시되지만 임의의 상위 카테고리에 속합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
