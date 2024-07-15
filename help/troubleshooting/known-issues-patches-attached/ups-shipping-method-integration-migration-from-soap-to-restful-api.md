---
title: ''' [!DNL SOAP] 에서  [!DNL RESTful API](으)로 ''[!DNL UPS] 배송 방법 통합 마이그레이션'''
promoted: true
description: Adobe Commerce 2.4.4 - 2.4.6-pX용  [!DNL UPS] 배송 방법 통합 마이그레이션을  [!DNL SOAP] 부터 [!DNL RESTful API] 까지 처리하려면 패치를 적용하십시오.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL SOAP]에서 [!DNL RESTful API](으)로 [!DNL UPS] 배송 방법 통합 마이그레이션

>[!NOTE]
>
>**2024년 6월 6일** 이전에 이 문서에서 세 개의 패치를 업로드한 경우: [!DNL Metric System/SI] 측정(킬로그램 및 센티미터)을 사용하지 않아 이 문제가 발생하는 경우, **[!DNL Admin configuration]**&#x200B;의 [!DNL UPS] 배송 방법에서 [!DNL Metric System/SI] 측정(**킬로그램** 및 **센티미터**)을 선택할 수 없으므로, 2.4.4+/2.4.5+/2.4.6+ 버전의 Adobe Commerce/Magento Open Source에 대해 이 문서에 게시된 새로운 업데이트된 패치 중 하나를 다시 적용해야 합니다. 이러한 새 패치는 이전에 릴리스된 패치와 호환됩니다. 이 문제는 **2024년 6월 11일**&#x200B;에 예정된 Adobe Commerce 버전 2.4.7-p1 릴리스의 범위에서 영구적으로 수정됩니다.

>[!NOTE]
>
>**2023년 10월 10일** 전에 이 문서에서 세 개의 패치를 업로드한 경우, 이제 이 문서에 게시된 이러한 패치 중 하나를 Adobe Commerce/Magento Open Source 2.4.4+/2.4.5+/2.4.6+ 버전에 다시 적용해야 합니다. 그렇지 않으면 **[!DNL Admin configuration]**&#x200B;에서 특정 [!DNL UPS] 배송 방법을 선택하고 구성할 수 없으므로 이러한 패치를 모두 활성화해야 합니다. 이러한 새 패치는 이전에 릴리스된 패치와 호환됩니다.

이 문서에서는 Adobe Commerce 2.4.4 - 2.4.6-pX에 대해 [!DNL SOAP]에서 [!DNL RESTful API](으)로 [!DNL United Parcel Service (UPS)] 배송 방법 통합 마이그레이션 문제를 해결하는 패치를 제공합니다.

[!DNL UPS API] 보안 모델의 최신 업데이트에 따라 [!DNL UPS]은(는) 모든 [!DNL APIs]에 대해 [!DNL OAuth 2.0] 보안 모델을 구현했습니다([[!DNL UPS] 개발자 포털 액세스 키 마이그레이션 안내서](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)에서 사용 가능한 세부 정보). 이를 통해 전체적인 보안을 강화하여 사기를 줄이고 향상된 [!DNL API] 기능을 제공합니다.

이 변경 사항은 Adobe Commerce의 현재 [!DNL UPS] 전달 방법 통합 구현에 영향을 미치며, 현재 구현을 수정하고 [!DNL OAuth 2.0] 인증 프로토콜을 지원할 수 있도록 [!DNL SOAP API]에서 [!DNL RESTful API](으)로 마이그레이션해야 합니다.

**2024년 6월부터**&#x200B;에서는 Adobe Commerce 판매자가 현재 [!DNL UPS] 통합과 거래할 수 없으므로 Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ 판매자가 최신 [!DNL UPS REST APIs](으)로 마이그레이션할 수 있도록 하는 이 핫픽스를 출시합니다.

이 문제는 Adobe Commerce/Magento Open Source 버전 2.4.7에서 수정되며, 이 수정 사항은 2023년 10월 2.4.7-beta2 릴리스에도 포함될 예정입니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure 및 on-premise 및 Magento Open Source:

* 2.4.4
* 2.4.4-pX
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## 원인

[!DNL UPS]이(가)  [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)에 대한 [보안 업데이트를 릴리스했습니다.

유럽 연합이 있는 경우(다른 원본에서 동일한 문제가 발생할 수 있음) [!DNL UPS REST] 요청에 오류가 발생합니다.
&quot;*선적은 측정 단위로 KGS/IN 또는 LBS/CM 또는 OZS/CM을 가질 수 없습니다.*&quot;

## 솔루션

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

2.4.4+, 2.4.5+ 및 2.4.6+ 버전에서 문제를 해결하려면 아래 Adobe Commerce/Magento Open Source 버전에 해당 패치를 적용해야 합니다.

## 패치

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

### 2.4.4, 2.4.4-pX 버전의 경우:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### 2.4.5, 2.4.5-pX 버전의 경우:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### 2.4.6, 2.4.6-pX 버전의 경우:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

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
