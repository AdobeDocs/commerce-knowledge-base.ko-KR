---
title: 'MDVA-31150: 스토어 크레딧 정보가 없는 인보이스'
description: MDVA-31150 패치는 저장소 신용 정보 없이 송장이 만들어지는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 수정됩니다.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150: 스토어 신용 정보가 없는 송장

MDVA-31150 패치는 저장소 신용 정보 없이 송장이 만들어지는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 수정됩니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.5-p2의 Adobe Commerce용으로 설계되었습니다.
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라 2.3.0 - 2.3.5-p2 및 2.4.0 - 2.4.0-p1과도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

API에 의한 송장 주문 후 사용된 고객 잔액 및 기프트 카드 정보가 송장에 없습니다.

<u>재현 단계</u>

1. 고객 계정에 스토어 크레딧 금액을 추가합니다. 관리 사이드바에서 **고객** > **모든 고객으로 이동합니다.**
1. 고객 레코드를 찾아 작업 열에서 **편집**&#x200B;을 클릭한 다음 **크레딧 저장** > 잔액 업데이트 > **고객 저장**&#x200B;을 클릭합니다.
1. Storefront로 이동하여 제품을 장바구니에 추가하십시오.
1. 매장 신용카드나 기프트 카드 금액을 부분 결제로 적용하여 주문합니다.
1. 페이로드가 있는 `REST API>POST>/rest/V1/order/1/invoice`을(를) 사용하여 인보이스 만들기:    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. `REST API>GET>/rest/V1/invoices/1`을(를) 사용하여 방금 만든 송장을 가져옵니다.

<u>예상 결과</u>

API 호출을 통해 스토어 신용 및 기프트 카드 잔액이 반환됩니다.

<u>실제 결과</u>

API 호출에서 스토어 신용 카드 및 기프트 카드 잔액을 반환하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
