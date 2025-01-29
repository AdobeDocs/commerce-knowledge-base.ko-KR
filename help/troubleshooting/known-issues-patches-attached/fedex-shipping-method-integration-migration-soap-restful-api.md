---
title: SOAP에서 RESTful API로 [!DNL FedEx] 배송 방법 통합 마이그레이션
promoted: true
description: Adobe Commerce 2.4.4-p4 - 2.4.6-pX용 SOAP에서 RESTful API로  [!DNL FedEx] 전달 방법 통합 마이그레이션을 처리하는 패치를 적용합니다.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7a54e992e365238ec7c764225a31cd3b6b8ad019
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# SOAP에서 RESTful API로 [!DNL FedEx] 배송 방법 통합 마이그레이션

>[!WARNING]
>
>이전에 제공한 패치 대신 [!DNL Quality Patches Tool](QPT) 1.1.57 릴리스의 ACSD-61622 패치를 사용하십시오. 새 패치는 Adobe Commerce 버전(모든 배포 방법) 2.4.6-p1 - 2.4.6-p8과 호환됩니다. 새로운 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 적용할 수 있습니다.
>
>자세한 내용은 Adobe Commerce 도구 안내서의 [ACSD-61622 패치 문서](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-61622-fedex-account-specific-rates-missing-from-response)를 참조하십시오.

>[!WARNING]
>
>새 패치를 설치하기 전에 이 문서에 제공된 이전 패치를 제거해야 합니다. 패치 제거에 대한 지침은 사용 안내서의 [사용자 지정 패치 되돌리기](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches#revert-a-custom-patch)를 참조하십시오.


이 문서에서는 Adobe Commerce 2.4.4-p4 - 2.4.6-pX용 SOAP에서 RESTful API로 [!DNL FedEx] 배송 방법 통합 마이그레이션 관련 문제를 해결하는 패치를 제공합니다.

[!DNL FedEx Web Services] 추적, 주소 유효성 검사 및 우편 번호 WSDLS(Validate Postal Codes Web Services Definition Languages)가 2024년 5월 15일에 사용이 중단되었습니다. SOAP 기반 [!DNL FedEx Web Services]이(가) 개발 억제 상태이며 [!DNL FedEx]개의 RESTFUL API로 대체되었습니다. 자세한 내용은 [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html)을(를) 참조하세요.

이 변경 사항은 Adobe Commerce의 현재 [!DNL FedEx] 전달 방법 통합 구현에 영향을 미치며, 현재 구현을 수정하고 더 이상 사용되지 않는 SOAP API에서 최신 [!DNL FedEx] RESTFUL API로 마이그레이션해야 합니다.

2024년 5월 15일부터 Adobe Commerce 고객은 현재 [!DNL FedEx] 배송 방법 통합을 사용할 수 없으므로 Adobe은 Adobe Commerce 2.4.4+ 고객이 더 이상 사용되지 않는 SOAP API 대신 최신 [!DNL FedEx] RESTFUL API를 사용할 수 있도록 하는 이 핫픽스를 출시합니다.


## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure 및 on-premise 및 Magento Open Source:

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## 원인

[!DNL FedEx]은(는) SOAP 기반 API를 더 이상 사용하지 않으며 대신 RESTful API로 대체되었습니다. [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html)을(를) 참조하세요.

## 솔루션

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

2.4.4+, 2.4.5+ 및 2.4.6+ 버전에서 문제를 해결하려면 아래 Adobe Commerce/Magento Open Source 버전에 해당 패치를 적용해야 합니다.

## 패치

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

### 버전 2.4.4-p4의 경우:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### 2.4.5, 2.4.5-pX 버전의 경우:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### 2.4.6, 2.4.6-pX 버전의 경우:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## 패치 적용 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)을 참조하십시오.

## 패치가 적용되었는지 확인하는 방법

문제가 패치되었는지 쉽게 확인할 수 없는 점을 고려하면 패치가 정상적으로 적용되었는지 확인할 수 있습니다. 확인할 패치로 (예: *AC-9363*) 사용합니다.

<u>다음 단계를 수행하여 이 작업을 수행할 수 있습니다</u>:

1. [설치 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. 다음 명령을 실행합니다.

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 다음과 유사한 출력이 표시되어야 합니다. 여기서 AC-9363은 *적용됨* 상태를 반환합니다.

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
