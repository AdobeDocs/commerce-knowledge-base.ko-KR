---
title: 'MDVA-28191: 관리자 새 주문 만들기에서 한 웹 사이트에 대한 결제 방법이 없음'
description: MDVA-28191 패치에서는 다른 웹 사이트에 결제 방법이 표시될 수 있지만 하나의 웹 사이트에 대해 관리**새 주문 만들기**에서 결제 방법이 로드되지 않는 문제가 해결되었습니다.  이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 도구 버전 1.0.5가 설치된 경우 사용할 수 있습니다.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191: 관리자 새 주문 만들기에서 한 웹 사이트에 대한 결제 방법이 없습니다.

MDVA-28191 패치는 결제 방법이 다른 웹 사이트에 표시될 수 있지만 하나의 웹 사이트에 대해 관리 **새 주문 만들기**&#x200B;에서 결제 방법이 로드되지 않는 문제를 해결합니다.  이 패치는 [QPT(품질 패치 도구)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 도구 버전 1.0.5가 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.3에서 2.4.1(2.3.5-p1 포함).

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

백엔드에서 주문을 생성할 때 Adobe Commerce에서 두 개의 견적을 생성하면 한 개의 견적이 비활성화되고 다른 하나의 견적이 활성화됩니다. 그러나 세션은 비활성 견적 ID를 보유합니다.

<u>재현 단계</u>

1. **관리 패널** > **판매** > **주문**(으)로 이동한 다음 **새 주문 만들기** 단추를 클릭합니다.
1. 주문을 생성할 고객을 선택합니다.
1. 스토어에 여러 개의 보기가 있는 경우 선택한 사용자에 대한 **새 주문 만들기** 페이지에서 주문을 넣을 스토어 보기를 선택하십시오.
1. **제품 추가**&#x200B;를 클릭하여 **고객의 활동** 섹션 또는 카탈로그에서 제품을 추가하십시오. 페이지를 아래로 스크롤하여 주문에 필요한 다음 섹션을 완료합니다.
   * 쿠폰 코드 적용
   * 결제 방법
   * 배송 방법
   * 주문 주석

<u>예상 결과:</u>

결제 방법은 모든 웹 사이트의 관리자에 로드되어야 합니다.

<u>실제 결과:</u>

다른 웹 사이트에 대한 주문을 테스트할 때 결제 방법이 표시될 수 있지만 이 웹 사이트에 사용할 수 있는 결제 방법이 없습니다(&quot;*결제 정보 필요 없음*&quot; 메시지가 표시되지 않음).

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
