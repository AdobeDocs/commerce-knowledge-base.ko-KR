---
title: Adobe Commerce 2.3.5의 제품 비교 알려진 문제
description: 이 문서에서는 Adobe Commerce 온-프레미스 2.3.5 및 Adobe Commerce 온 클라우드 인프라 2.3.5에서 알려진 [제품 비교](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare) 문제를 방지하는 방법에 대한 권장 사항을 제공합니다.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Adobe Commerce 2.3.5의 제품 비교 알려진 문제

이 문서에서는 Adobe Commerce 온-프레미스 2.3.5 및 Adobe Commerce 온-클라우드 인프라 2.3.5의 알려진 [제품 비교](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare) 문제를 방지하는 방법에 대한 권장 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.3.5
* 클라우드 인프라의 Adobe Commerce 2.3.5

## 문제

사용자가 다른 스토어 보기의 제품을 비교하려고 할 때 한 제품에 비교 가능한 속성에 대한 값이 비어 있으면 Adobe Commerce에 손상된 제품 비교 페이지가 표시됩니다.

## 솔루션

비교 가능한 제품 속성에 대해 비어 있지 않은 값을 지정하거나 속성에 대해 기본 스토어 보기 값을 사용합니다. 비교 가능한 속성 값은 비워 둘 수 없습니다.

>[!NOTE]
>
>제품 특성은 **Comparable on Storefront** 구성 설정을 사용하여 비교하는 데 사용하도록 설정되어 있습니다. 자세한 내용은 사용 안내서의 [제품 특성 만들기](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create#step-4-describe-the-storefront-properties)를 참조하세요.

수정 사항은 2020년 4분기에 릴리스될 예정인 Adobe Commerce 2.3.6에서 사용할 수 있습니다.

GitHub에서 수정 사항을 볼 수 있습니다(해당 수정 사항이 회귀 테스트를 거치지 않았으며 공식 핫픽스가 아님을 고려). <https://github.com/magento/magento2/pull/27662>

## 관련 읽기

<ul><li>Adobe Commerce 2.3.5의 알려진 문제에 대한 Adobe Commerce 지원 기술 문서<ul>
<li>
<p title="Adobe Commerce 2.3.5에서 가상 제품이 올바르게 처리되지 않는 다중 배송 주문"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Adobe Commerce 2.3.5에서 가상 제품이 올바르게 처리되지 않는 다중 배송 주문</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Adobe Commerce 2.3.5의 대량 작업 제품 수 알려진 문제</a></li>
<li>
<p title="Amazon용 패치 Adobe Commerce 2.3.5-p1 의 결제 체크아웃 문제"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Amazon용 패치 Adobe Commerce 2.3.5-p1 의 결제 체크아웃 문제</a></p>
</li>
</ul>
</li><li>개발자 설명서의 <a href="https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Adobe Commerce 2.3.5 알려진 문제</a></li></ul>
