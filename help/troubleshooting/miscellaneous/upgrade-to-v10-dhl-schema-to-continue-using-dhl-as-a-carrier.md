---
title: v10 DHL 스키마로 업그레이드하여 DHL 배송 계속
description: 이 문서에서는 DHL 스키마 6.2가 2022년 12월에 사용 중단되거나 스키마 10.0으로 업그레이드하거나 AC-3023 패치를 적용하여 판매자가 DHL 배송을 계속 제공할 수 있도록 하는 솔루션을 제공합니다.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# 버전 10.0 DHL 스키마로 업그레이드하여 DHL 배송 계속

이 문서에서는 DHL 스키마 버전 6.2가 2022년 12월 말에 더 이상 사용되지 않는 후에도 상인이 DHL 배송을 계속 제공할 수 있도록 하는 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.5 및 이전 버전, 모든 배포 메서드.

## 문제

2022년 8월에 판매자가 DHL 배송을 계속 제공할 수 있도록 [DHL 스키마 버전 6.2의 업그레이드 및 수정 패치](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html)를 릴리스했습니다. DHL은 2022년 10월에 새로운 스키마(버전 10.0)를 다시 도입했으며 이전 버전(6.2 스키마)은 2022년 12월 말에 더 이상 사용되지 않을 예정입니다. Adobe Commerce 2.4.5 및 이전 버전의 DHL 통합은 버전 6.2만 지원합니다.

## 솔루션

2022년 10월에 릴리스된 Adobe Commerce 2.4.5-p1 및 2.4.4-p2에는 새 DHL 스키마 버전 10.0이 포함되어 있습니다. 따라서 2.4.5-p1 및 2.4.4-p2로 업그레이드하는 상인은 DHL 배송을 계속 제공하기 위해 아무것도 할 필요가 없습니다. 모든 판매자는 2022년 12월 말 DHL 스키마 6.2가 더 이상 사용되지 않기 전에 2.4.5-p1 및 2.4.4-p2로 업그레이드할 것을 권장합니다.

2.4.5-p1 및 2.4.4-p2로 업그레이드하지 않으려는 판매자는 2022년 12월 이후에도 DHL 배송을 계속 제공하려면 수정 패치를 적용해야 합니다.

## 패치

패치 ID는 AC-3023이며 [!DNL Quality Patches Tool] 버전 1.1.21에서 사용할 수 있습니다.

배포 방법에 따라 [!DNL Quality Patches Tool]을(를) 사용하고 패치를 설치하는 방법에 대한 다음 링크를 참조하세요.

* Adobe Commerce 온-프레미스 및 Magento Open Source: Adobe Experience League의 [품질 패치 도구 > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

**패치는 다음 Adobe Commerce 버전(모든 배포 방법)에 적용됩니다.**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## 유용한 링크

* Adobe Experience League의 [[!DNL Quality Patches Tool] > 릴리스 정보](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html).

* [[!DNL Quality Patches Tool]: Adobe Experience League에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 패치를 검색합니다.

## 관련 읽기

* 지원 기술 자료에서 [DHL을 배송 운송업체로 계속 제공하려면 패치를 적용하세요](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html).

* 사용 안내서의 [운송업체 > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html).
* 사용 안내서의 [구성 참조 > 판매 > 게재 방법](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html).
