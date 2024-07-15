---
title: 'MDVA-30972: 주문 상태가 REST API를 통해 잘못된 선적을 만들었습니다.'
description: MDVA-30972 패치는 REST API를 통해 배송을 생성하는 동안 주문 상태가 잘못 변경되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: REST API를 통해 생성된 주문 상태 잘못된 배송

MDVA-30972 패치는 REST API를 통해 배송을 생성하는 동안 주문 상태가 잘못 변경되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0에서 2.4.2로

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 상태가 *사기 혐의임*&#x200B;인 주문에 대해 REST API를 통해 관리자로부터 부분 선적이 만들어지면 주문 상태가 *처리*(으)로 변경됩니다. *사기 의심*&#x200B;에 있어야 합니다.

<u>필수 구성 요소</u>:

* PayPal EC 또는 다른 온라인 결제 방법을 설정합니다.
* REST API에 대한 통합이 설정되었습니다.

<u>재현 단계</u>:

1. 두 개 이상의 항목으로 주문을 만듭니다.
1. **관리자** > **판매** > **주문**&#x200B;에 로그인합니다. 방금 생성한 주문을 엽니다.
1. 주문 세부 정보 페이지에서 **주문 총계**(으)로 스크롤합니다. **상태** 드롭다운을 클릭하고 *사기 행위가 의심되는*&#x200B;을(를) 선택합니다. **댓글 제출** 단추를 클릭합니다.
1. 이제 주문의 상태가 *사기 행위가 의심되는*&#x200B;인지 확인하세요.
1. REST API를 사용하여 주문에서 한 품목에 대한 납품을 생성합니다.

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Admin에서 주문을 다시 열고 상태를 확인합니다.

<u>예상 결과</u>:

* 주문 상태 = *사기 행위가 의심됨*.
* 동일한 선적이 책임자로부터 생성된 경우 주문 상태가 변경되지 않습니다.

<u>실제 결과</u>:

주문 상태 = *처리 중*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
