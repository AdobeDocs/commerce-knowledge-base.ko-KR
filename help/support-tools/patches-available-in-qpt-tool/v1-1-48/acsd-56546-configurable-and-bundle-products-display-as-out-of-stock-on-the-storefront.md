---
title: 'ACSD-56546: 구성 및 번들 제품이 상점 앞에 품절로 표시됨'
description: ACSD-56546 패치를 적용하여 *[!UICONTROL Display Out of Stock Products]* 구성 옵션이 비활성화될 때 구성 가능 및 번들 제품이 상점 첫 화면에서 품절로 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: 구성 및 번들 제품이 상점 앞에 품절로 표시됨

ACSD-56546 패치는 구성 가능 및 번들 제품이 상점 첫 화면에서 품절로 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56546입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Display Out of Stock Products]* 옵션이 비활성화되면 구성 가능한 번들 제품이 상점 앞에 품절로 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Display Out of Stock Products]** 옵션을 *아니요*(으)로 설정하십시오.
1. 웹 사이트, 스토어 및 스토어를 만듭니다.
1. 소스 및 스톡을 만든 다음 두 번째 웹 사이트에 할당합니다.
1. 두 개의 하위 제품이 있는 *구성 가능한 제품*&#x200B;을 만듭니다. 하위 제품을 소스와 웹 사이트 모두에 할당합니다.
1. 두 원본 모두에서 *qty=0*&#x200B;을(를) 갖도록 첫 번째 하위 제품을 업데이트하십시오.
1. 두 번째 하위 제품을 업데이트하고 두 번째 웹 사이트에서 비활성화합니다.
1. 전체 색인 재지정을 수행합니다.
1. 두 번째 웹 사이트에서 구성 가능한 제품이 포함된 카테고리를 확인하십시오.

<u>예상 결과</u>:

품절 구성 가능 제품은 상점 앞에 표시되지 않습니다.

<u>실제 결과</u>:

*[!UICONTROL Display Out of Stock Products]* 옵션을 사용하지 않도록 설정한 경우에도 재고 부족 구성 가능한 제품이 상점 앞에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
