---
title: 'MDVA-37082: 그룹화된 제품에 대한 재고 상태의 부분 색인이 잘못됨'
description: MDVA-37082 Magento 패치는 그룹화된 제품에 대한 재고 상태의 부분 색인이 사용자 정의 주식에 대해 잘못된 경우 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37082입니다. 이 문제는 Magento 2.4.4에서 수정됩니다.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082: 그룹화된 제품에 대한 재고 상태의 부분 색인이 잘못되었습니다.

MDVA-37082 Magento 패치는 그룹화된 제품에 대한 재고 상태의 부분 색인이 사용자 정의 주식에 대해 잘못된 경우 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37082입니다. 이 문제는 Magento 2.4.4에서 수정됩니다.


## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.3.4-p2

**Adobe Commerce 버전과 호환:**
Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.4.2-p1
>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

그룹화된 제품 하위 제품을 증분 색인화하면 하위 제품을 공유할 때 잘못된 다른 그룹화된 제품이 잘못 색인화될 수 있습니다.

<u>재현 단계</u>:

* 기본 웹 사이트에 대한 새 주식과 소스를 만듭니다.
* 수량 10, 15 및 0으로 3개의 간단한 제품을 만듭니다.
* 2개의 그룹화된 제품을 만들고 첫 번째 단순 제품과 수량 10부터 1까지, 그리고 다른 2개의 단순 제품을 할당합니다.
* 그룹화된 두 제품 모두 프론트엔드에서 재고로 액세스할 수 있는지 확인합니다.
* 수량이 0인 간단한 제품을 첫 번째로 그룹화된 제품의 상향 판매 제품에 지정합니다.
* 전체 페이지 캐시를 지우고 프론트엔드에서 두 번째 그룹화된 제품을 확인합니다.
* 전체 다시 색인을 실행합니다.
* 프론트엔드에서 두 번째 그룹화된 제품을 확인하십시오.
* 첫 번째로 그룹화된 제품을 저장합니다.
* 전체 페이지 캐시를 지우고 프론트엔드에서 두 번째 그룹화된 제품을 확인합니다.

<u>예상 결과</u>:

상향 판매로 다른 그룹화된 제품을 저장한 후 그룹화된 제품이 품절되지 않았습니다. 이 문제는 전체 색인 재지정 후에 해결됩니다.

<u>실제 결과</u>:

두 번째 묶은 제품은 첫 번째 묶은 제품을 저장하면 품절됩니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 배포 방법에 따라 개발자 설명서에 대한 다음 링크를 사용하십시오.

* Adobe Commerce 온-프레미스: 개발자 설명서에서 [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Magento 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
