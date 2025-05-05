---
title: 'MDVA-40609: 비활성화된 제품 데이터가 cataloginventory_stock_status 테이블에 없음'
description: MDVA-40609 패치는 잘못된 제품 수량을 표시하는 'cataloginventory_stock_status' 색인 테이블에 비활성화된 제품 데이터가 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40609입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: 비활성화된 제품 데이터가 cataloginventory_stock_status 테이블에 없음

MDVA-40609 패치는 비활성화된 제품 데이터가 `cataloginventory_stock_status` 인덱스 테이블에 표시되지 않아서 잘못된 제품 수량이 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40609입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

비활성화된 제품 데이터가 `cataloginventory_stock_status` 인덱스 테이블에 표시되지 않아서 잘못된 제품 수량이 표시됩니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 스토어 및 스토어 조회수를 제공하는 웹 사이트 두 개를 설정합니다.
1. 추가 소스 및 재고를 생성합니다.
1. 간단한 제품 추가:
   * 제품 사용을 *아니요*(으)로 설정합니다.
   * Source 품목 상태 = 재고 및 수량이 0보다 큰 두 소스를 지정합니다.
1. 제품을 저장합니다.
1. **제품 판매 수량** 탭을 확인하십시오.

<u>예상 결과</u>:

두 주식 모두 0보다 큰 값을 입력했습니다.

<u>실제 결과</u>:

하나의 스톡 값은 0입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
