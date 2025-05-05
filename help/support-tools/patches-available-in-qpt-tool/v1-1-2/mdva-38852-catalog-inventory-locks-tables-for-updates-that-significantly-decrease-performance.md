---
title: 'MDVA-38852: 카탈로그 인벤토리가 테이블을 잠그므로 성능이 저하됨'
description: MDVA-38852 패치는 카탈로그 인벤토리가 업데이트에 대해 테이블을 잠그는 문제를 해결하여 여러 병렬 주문이 배치될 때 성능을 크게 저하시킵니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38852입니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.
exl-id: 6ecee9c8-1f39-47de-8fbc-55e30cc936af
feature: Catalog Management, Inventory, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-38852: 카탈로그 인벤토리가 테이블을 잠그므로 성능이 저하됩니다.

MDVA-38852 패치는 카탈로그 인벤토리가 업데이트에 대해 테이블을 잠그는 문제를 해결하여 여러 병렬 주문이 배치될 때 성능을 크게 저하시킵니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38852입니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카탈로그 인벤토리는 여러 병렬 주문이 있는 경우 성능을 크게 저하시키는 업데이트에 대해 테이블을 잠급니다.

<u>재현 단계</u>:

1. 장바구니에 제품을 추가합니다.
1. 체크아웃을 진행하고 주문해 보십시오.

<u>예상 결과</u>:

* 교착 상태가 없습니다.
* 여러 개의 병렬 주문이 이루어진 경우에는 성능이 저하되지 않는다.

<u>실제 결과</u>:

* 동시 사용자가 여러 명인 경우 주문이 매우 느립니다.
* 다음과 같은 교착 상태 오류가 발생합니다.

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
