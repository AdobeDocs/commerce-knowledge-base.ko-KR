---
title: 'MDVA-26639: 새 주문 확인 전자 메일 템플릿에 주문 항목이 없습니다.'
description: MDVA-26639 패치는 새 주문을 만들 때 주문 항목이 확인 이메일 템플릿에 누락되는 문제를 해결합니다.
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639: 새 주문 확인 전자 메일 템플릿에 주문 항목이 없습니다.

MDVA-26639 패치는 새 주문을 만들 때 주문 항목이 확인 이메일 템플릿에 누락되는 문제를 해결합니다.

이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치되어 있습니다. 패치 ID는 MDVA-26639입니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.3.3-p1

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 다음으로 이동 **스토어** > **구성** > **판매** > **영업 이메일** > **새 주문 확인** 및 선택 **템플릿: 새 픽업 주문**.
1. 다음으로 이동 **판매** > **주문: 주문 선택**&#x200B;로 이동한 다음 로 이동합니다. **정보**, 및 선택 **메일 보내기**.

<u>예상 결과</u>:

주문 항목은 예상대로 고객 주문 이메일에 표시됩니다.

<u>실제 결과</u>:

고객 주문 이메일에 주문 항목이 누락되었습니다. 새 템플릿을 만들고 템플릿 새 순서 또는 새 순서(Luma)를 선택하는 경우에도 마찬가지입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
