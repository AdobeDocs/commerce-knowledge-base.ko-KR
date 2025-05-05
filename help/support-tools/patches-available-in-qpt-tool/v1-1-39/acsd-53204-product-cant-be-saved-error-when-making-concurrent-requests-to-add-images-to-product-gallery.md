---
title: 'ACSD-53204: *제품을 저장할 수 없음* 갤러리에 이미지 추가 동시 요청 시 오류 발생'
description: ACSD-53204 패치를 적용하여 *제품을 저장할 수 없는* rest/V1/products/&lt;sku&gt;/media 종단점을 사용하여 제품 갤러리에 이미지를 추가하도록 동시에 요청할 때 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204: 갤러리에 이미지를 추가하기 위한 동시 요청 시 &quot;*제품을 저장할 수 없습니다*&quot; 오류 발생

ACSD-53204 패치는 `rest/V1/products/<sku>/media` 끝점을 사용하여 제품 갤러리에 이미지를 추가하는 동시 요청을 할 때 &quot;*제품을 저장할 수 없습니다*&quot; 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.39가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53204입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`rest/V1/products/<sku>/media` 끝점을 사용하여 제품 갤러리에 이미지를 추가하도록 동시에 요청할 때 &quot;*제품을 저장할 수 없습니다*&quot; 오류가 발생합니다.

<u>재현 단계</u>:

1. 관리 패널에 로그인합니다.
1. SKU p1로 제품을 만듭니다.
1. 여러 이미지를 동시에 업로드하려면 `rest/V1/products/<sku>/media` 끝점에 대한 여러 개의 동시 요청을 만듭니다.

<u>예상 결과</u>:

이미지는 오류 없이 저장됩니다.

<u>실제 결과</u>:

&quot;*제품을 저장할 수 없습니다*&quot; 오류가 수시로 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
