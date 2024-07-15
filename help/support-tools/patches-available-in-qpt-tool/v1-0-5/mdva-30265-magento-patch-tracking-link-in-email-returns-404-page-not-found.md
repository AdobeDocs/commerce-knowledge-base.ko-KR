---
title: 'MDVA-30265: 이메일의 추적 링크가 404 페이지를 찾을 수 없음'
description: MDVA-30265 패치는 고객이 주문 확인 이메일에서 배송 추적 링크를 클릭할 때 발생하는 '404 페이지를 찾을 수 없음' 오류 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265: 이메일의 추적 링크가 404 페이지를 찾을 수 없음

MDVA-30265 패치는 고객이 주문 확인 이메일에서 배송 추적 링크를 클릭할 때 발생하는 &#39;404 페이지를 찾을 수 없음&#39; 오류 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3에서 2.4.1로

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문에 대한 배송이 생성되면 주문 추적을 위한 추적 정보와 링크가 포함된 이메일이 고객에게 전송됩니다. 그러나 고객이 이메일에서 배송 추적 링크를 클릭하면 &quot;404 페이지를 찾을 수 없음&quot; 오류가 반환됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 2.4 설치 단계는 개발자 설명서에서 [작성기를 사용하여 Adobe Commerce 설치](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html)를 참조하십시오.
1. 주문하십시오.
1. 관리 패널 > **판매** > **주문**(으)로 이동합니다. 방금 만든 주문을 찾아 엽니다.
1. 선적을 생성하고 추적 번호를 추가합니다(운송회사 = 사용자 정의 값). 단계는 사용 안내서의 [Order Management > 배송 만들기](https://docs.magento.com/user-guide/sales/shipments-create.html)를 참조하십시오.
1. 이메일을 받습니다. 추적 링크를 클릭하여 작동하는지 확인합니다.
1. 송장을 생성합니다. 단계는 사용 안내서의 [Order Management > 송장 만들기](https://docs.magento.com/user-guide/sales/invoice-create.html)를 참조하십시오. 그런 다음 위의 추적 링크를 다시 클릭합니다.

<u>예상 결과</u>:

추적 링크는 송장을 만든 후에도 작동해야 합니다.

<u>실제 결과</u>:

송장을 만든 후 추적 링크가 작동하지 않고 &quot;404 페이지를 찾을 수 없음&quot; 오류 페이지를 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
