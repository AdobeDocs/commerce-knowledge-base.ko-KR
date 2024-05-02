---
title: "MDVA-39482: 미납주문을 활성화한 상태에서 수량을 '0'으로 가져온 경우 제품이 품절 됨"
description: MDVA-39482은 MSI 및 미납 주문이 활성화되어 있고 재고 부족 임계값이 마이너스 값으로 설정된 경우 "0" 수량으로 제품을 가져올 경우 제품이 품절되는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39482입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482: 미납주문을 활성화한 상태에서 수량을 &#39;0&#39;으로 하여 제품을 가져오면 제품이 품절됩니다.

MDVA-39482은 MSI 및 미납 주문이 활성화되어 있고 재고 부족 임계값이 마이너스 값으로 설정된 경우 &quot;0&quot; 수량으로 제품을 가져올 경우 제품이 품절되는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4가 설치되었습니다. 패치 ID는 MDVA-39482입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

Adobe Commerce(모든 배포 방법) 2.4.1-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

MSI 및 미납주문 수가 활성화되고 재고 부족 임계값이 마이너스 값으로 설정된 경우 제품을 &quot;0&quot; 수량으로 가져오면 제품이 품절됩니다.

<u>전제 조건</u>:

1. MSI 및 샘플 데이터가 설치되어 있어야 합니다.
1. 다음으로 이동 **스토어** > **구성** > **카탈로그** > **인벤토리**:
   * 미납주문을 &quot;0 이하 수량 허용&quot;으로 설정
   * 품절 임계값을 &quot;-10&quot;으로 설정

<u>재현 단계</u>:

1. SKU가 **재고 있음** 및 수량 **24MB01**.
1. Stock 소스의 CSV를 가져옵니다. 엔티티 유형에서 &quot;Stock 소스&quot;를 선택해야 합니다.

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Stock 소스를 가져온 후 제품의 재고 상태를 확인합니다.

<u>예상 결과</u>:

24MB01 **재고 있음** 상점 앞에서.

<u>실제 결과</u>:

24MB01 **품절** 상점 앞에서.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
