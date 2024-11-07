---
title: 'MDVA-42790: REST API를 통해 특정 웹 사이트에 대해 제품 가격 특성을 업데이트할 수 없음'
description: MDVA-42790 패치는 사용자가 REST API를 통해 특정 웹 사이트에 대한 제품 가격 속성을 업데이트할 수 없는 문제를 수정했습니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42790입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: b9d80190-17d2-436f-86d5-33689b8224d4
feature: REST, Attributes, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-42790: REST API를 통해 특정 웹 사이트에 대해 제품 가격 특성을 업데이트할 수 없습니다.

MDVA-42790 패치는 사용자가 REST API를 통해 특정 웹 사이트에 대한 제품 가격 속성을 업데이트할 수 없는 문제를 수정했습니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42790입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자는 REST API를 통해 특정 웹 사이트에 대한 제품 가격 속성을 업데이트할 수 없습니다.

<u>재현 단계</u>:

1. 관리자의 경우 **스토어** > **구성** > **카탈로그** > **가격** >(으)로 이동하고 웹 사이트에 **카탈로그 가격 범위**&#x200B;를 설정합니다.
1. REST API, `POST rest/V1/products/`을(를) 사용하여 번들 제품의 특별 가격을 업데이트합니다.

   ```JSON
   {
     "product": {
       "id": 46,
       "sku": "24-WG080",
       "name": "Sprite Yoga Companion Kit",
       "attribute_set_id": 4,
       "price": 10,
       "status": 1,
       "visibility": 1,
       "type_id": "bundle",
       "weight": 0,
       "custom_attributes": [
         {
           "attribute_code": "special_price",
           "value": "2"
         }
       ]
     }
   }
   ```

<u>예상 결과</u>:

**카탈로그 가격 범위**&#x200B;가 웹 사이트로 설정된 경우 번들 제품에 대한 특별 가격이 업데이트됩니다.

<u>실제 결과</u>:

**카탈로그 가격 범위**&#x200B;가 웹 사이트로 설정된 경우 번들 제품에 대한 특별 가격이 업데이트되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
