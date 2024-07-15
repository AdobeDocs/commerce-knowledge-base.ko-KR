---
title: 'MDVA-28763: REST API를 통해 제품 이미지 관리 문제'
description: MDVA-28763 패치는 REST API를 사용한 미디어 갤러리 관리와 관련된 여러 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우 사용할 수 있습니다. 이 문제는 이후 Adobe Commerce 버전에서 수정되도록 예약되었습니다.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763: REST API를 통한 제품 이미지 관리 문제

MDVA-28763 패치는 REST API를 사용한 미디어 갤러리 관리와 관련된 여러 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우에 사용할 수 있습니다. 문제는 이후 Adobe Commerce 버전에서 수정되도록 예약되었습니다([문제](#issues)의 문제 설명 참조).

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce 온-프레미스 2.3.2 - 2.3.3.x
* 클라우드 인프라의 Adobe Commerce 2.3.2 - 2.3.3.x

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제 {#issues}

MDVA-28763 패치에는 미디어 갤러리와 관련된 다음 문제에 대한 수정 사항이 포함되어 있습니다.

* REST API를 사용하여 YouTube 비디오(`PUT rest/V1/products/ {SKU}`)를 업데이트할 때 Adobe Commerce에 비디오의 썸네일이 표시되지만, &quot;재생&quot; 단추를 클릭할 때 비디오 플레이어가 로드되지 않습니다. Adobe Commerce 2.3.6에서 수정되도록 예약되었습니다.
* `PUT /V1/products/:sku/media/:entryId` 호출은 기존 항목을 대체하지 않고 새 항목을 만듭니다. Adobe Commerce 2.3.5에서 해결되었습니다.
* 제품이 여러 스토어 보기에 할당될 때 제품 이미지가 삭제되는 문제가 발생합니다. Adobe Commerce 2.3.4에서 해결되었습니다.
* 이제 여러 웹 사이트를 보유한 판매자는 이미지 및 이미지 역할 상속을 유지하면서 REST를 사용하여 제품을 만들고 업데이트할 수 있습니다. 이전에는 판매자가 REST를 사용하여 제품을 만들고 업데이트한 경우 스토어 보기에 대해 제품이 업데이트되면 해당 스토어 보기에 대해 기본 이미지 역할이 로드 및 저장되었습니다. 따라서 업데이트 후 저장소 보기 이미지 역할이 기본 범위에서 상속을 중지합니다. Adobe Commerce 2.3.6에서 수정되도록 예약되었습니다.
* 미디어 속성(이미지, 썸네일, ...) 제거된 이미지를 참조하는 저장소 보기의 값이 자동으로 정리되지 않습니다. Adobe Commerce 2.4.2에서 수정되도록 예약되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
