---
title: '[!DNL USPS] AC-9182용 Ground Advantage 배송 방법 지원 핫픽스'
promoted: true
description: Adobe Commerce 2.4.4 - 2.4.6-p2용  [!DNL USPS] Ground Advantage 배송 방법 문제 AC-9182를 해결하기 위해 패치를 적용합니다.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] AC-9182용 Ground Advantage 배송 방법 지원 핫픽스

이 문서에서는 Adobe Commerce 2.4.4 - 2.4.6-p2의 새로운 **[!DNL USPS]기반 이점** 배송 방법에 대한 문제 AC-9182를 해결하기 위한 패치를 제공합니다.

2023년 7월 9일, 미국 우편 서비스([!DNL USPS])에서 새로운 배송 방법인 [[!DNL USPS] 기본 이점](https://www.usps.com/ship/ground-advantage.htm)을 발표했습니다.

이 새로운 배송 방법은 다음과 같은 세 가지 주요 배송 방법을 대체하고 있습니다.

* [!DNL USPS] 소매 기반
* [!DNL USPS] 퍼스트 클래스 패키지 서비스
* [!DNL USPS]개 택배 그라운드 선택

[[!DNL USPS] 2023년 9월 30일부터 이 세 가지 배송 방법이 중단되며 모든 고객은 새로운 **[!DNL USPS]기반 이점** 방법을 대신 사용해야 한다고 발표](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works).

따라서 2023년 9월 30일 이후에는 USPS 배송 방법을 사용 중인 모든 Adobe Commerce 가맹점이 이 세 가지 기존 배송 방법을 사용하여 [!DNL USPS]에서 더 이상 배송 요금을 받을 수 없습니다.

이 문제는 2023년 10월에 예정된 보안 전용 패치 릴리스의 범위(버전 2.4.6-p3, 2.4.5-p5 및 2.4.4-p6)에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure 및 on-premise 및 Magento Open Source:

* 2.4.4
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2.4.5
* 2.4.5-p1
* 2.4.5-p2
* 2.4.5-p3
* 2.4.5-p4
* 2.4.6
* 2.4.6-p1
* 2.4.6-p2

## 원인

[!DNL USPS]에서 [!DNL API]을(를) 업데이트했습니다.

## 솔루션

2.4.4, 2.4.5 및 2.4.6 버전에서 이 문제를 해결하려면 아래의 AC-9182 패치를 적용해야 합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 다음 링크를 클릭하십시오.

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## 패치 적용 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=ko)을 참조하십시오.

## 패치가 적용되었는지 확인하는 방법

문제가 패치되었는지 쉽게 확인할 수 없는 점을 고려하면 AC-9182 패치가 성공적으로 적용되었는지 확인할 수 있습니다.

<u>다음 단계를 수행하여 이 작업을 수행할 수 있습니다</u>:

1. [설치 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko).
1. 다음 명령을 실행합니다.

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. 다음과 유사한 출력이 표시되어야 합니다. 여기서 AC-9182는 *적용됨* 상태를 반환합니다.

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
