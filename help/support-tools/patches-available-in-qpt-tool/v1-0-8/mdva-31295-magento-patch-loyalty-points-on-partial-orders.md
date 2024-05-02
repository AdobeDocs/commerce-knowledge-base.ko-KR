---
title: 'MDVA-31295: 부분 주문에 대한 충성도 포인트'
description: MDVA-31295 패치는 부분 주문이 완료되고 항목이 과세될 때 보상 포인트가 올바르게 계산되지 않는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295: 부분 주문에 대한 충성도 포인트

MDVA-31295 패치는 부분 주문이 완료되고 항목이 과세될 때 보상 포인트가 올바르게 계산되지 않는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치되었습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce 온-프레미스 2.3.0

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문이 완료(부분 배송)되고 품목이 과세될 때는 고객의 계정에 보상이 적용되지 않는다. 항목이 과세되지 않는 경우 보상이 성공적으로 고객의 계정에 추가됩니다.

<u>재현 단계</u>:

1. storefront에 고객으로 로그인합니다.
1. 장바구니에 두 제품을 추가합니다.
1. 체크아웃으로 가서 세금이 있는 배송지 주소를 설정하고 주문을 합니다.
1. 관리자에서 최근에 주문한 주문으로 이동합니다.
1. 클릭 **인보이스** 및 설정 **송장 수량** 항목 중 하나에 대해 0으로 설정하고 **업데이트 수량**. 송장을 실행합니다.
1. 출하 및 설정 클릭 **납품할 수량** 송장이 발행되지 않은 품목에 대해 0으로 설정합니다. 클릭 **배송 제출**.
1. 주문 취소를 누릅니다. 상태는 완료로 설정됩니다.
1. 관리자 권한으로 **고객** > > 이전에 수행한 고객 구매 선택 > **보상 점수** > **보상 포인트 내역**.
1. 주문한 주문에 대해 획득한 보상 포인트를 확인합니다.

<u>예상 결과</u>:

부분 주문이 완료될 때 과세 주문에 대한 보상 포인트를 계산해야 합니다.

<u>실제 결과</u>:

부분 주문이 완료될 때 과세 주문에 대한 보상 포인트는 계산되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
