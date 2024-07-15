---
title: 'MDVA-42584: 구성 가능한 제품의 재고 상태가 자동으로 업데이트되지 않음'
description: MDVA-42584 패치는 구성 가능한 제품의 단순 제품이 업데이트될 때 재고 상태가 자동으로 업데이트되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42584입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: 구성 가능한 제품의 재고 상태가 자동으로 업데이트되지 않음

MDVA-42584 패치는 구성 가능한 제품의 단순 제품이 업데이트될 때 재고 상태가 자동으로 업데이트되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42584입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

API 또는 가져오기를 통해 간단한 제품이 **재고 중**(으)로 설정된 경우 백엔드에서 구성 가능한 제품의 재고 상태가 자동으로 업데이트되지 않습니다.

<u>필수 구성 요소</u>:

MSI가 설치되었습니다.

<u>재현 단계</u>:

1. **InvCheck001-M** 및 **InvCheck001-L** 옵션을 사용하여 구성 가능한 제품 **InvCheck001**&#x200B;을 만듭니다.
1. 구성 가능한 제품이 백엔드에서 **재고 중**&#x200B;이 되도록 단순 제품 모두에 수량이 있고 **재고 중**&#x200B;이어야 합니다.
1. 이제 간단한 제품을 모두 업데이트하고 수량을 **0**(으)로 설정하고 재고 상태를 **재고 부족**(으)로 설정합니다.
1. 구성 가능한 제품을 새로 고치고 재고 상태가 **재고 부족**(으)로 업데이트되었는지 확인하십시오.
1. 다음 API 끝점을 사용하고 단순 제품 **InvCheck001-M**&#x200B;을(를) 수량 > 0인 **재고**(으)로 설정하십시오.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. 백엔드로 이동하여 단순 제품 **InvCheck001-M**&#x200B;의 수량 및 재고 상태를 확인합니다. **재고 중**(으)로 업데이트되었습니다.
1. 구성 가능한 제품을 새로 고치고 재고 상태를 확인합니다.

<u>예상 결과</u>:

백엔드에서 구성 가능한 제품 **InvCheck001**&#x200B;의 재고 상태가 **재고 중**(으)로 자동 업데이트됩니다.

<u>실제 결과</u>:

구성 가능한 제품의 재고 상태가 여전히 **재고 부족**&#x200B;입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
