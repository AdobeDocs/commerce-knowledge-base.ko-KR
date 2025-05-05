---
title: "ACSD-51846:  [!DNL REST API] 페이로드 수준의 유효성을 검사하지 않아 내부 오류가 발생했습니다."
description: ACSD-51846 패치를 적용하여  [!DNL REST API] 페이로드의 모든 수준이 확인되지 않아 "내부 오류"가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: REST
role: Developer
exl-id: 17ce5cca-063d-439c-9390-f5e2bf5b696b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51846: [!DNL REST API] 페이로드 수준의 유효성을 검사하지 않아 내부 오류 발생

ACSD-51846 패치는 [!DNL REST API] 페이로드의 모든 수준이 확인되지 않아 &quot;내부 오류&quot;가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51846입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL REST API] 페이로드의 모든 수준이 확인되지 않으므로 &quot;내부 오류&quot;가 발생합니다.

<u>재현 단계</u>:

1. 고객의 장바구니에 제품을 추가합니다.
1. 잘못된 특성 &quot;_street&quot;을(를) 사용하여 [!DNL REST API] 요청을 `rest/V1/carts/mine/estimate-shipping-methods`에 보냅니다.끝에 점이 있는_&quot;

```
 {
    "address": {
         "street.": [
             "\uc11c\uc6b8 \uac15\ubd81\uad6c \ud55c\ucc9c\ub85c166\uae38 2 (-\uc11c\uc6b8 \uac15\ubd81\uad6c \uc218\uc720\ub3d9 269-36)"
         ],
         "city": "pune",
         "region": null,
         "country_id": "IN",
         "postcode": "411015",
         "customer_id": "2",
         "firstname": "test",
         "lastname": "test",
         "middlename": null,
         "prefix": null,
         "suffix": null,
         "vat_id": null,
         "company": null,
         "telephone": "00000000000",
         "fax": null,
         "custom_attributes": []
     }
 }
```

<u>예상 결과</u>:

끝점은 매개 변수의 유효성을 검사하고 특정 오류 메시지와 함께 `400 status code`을(를) 반환해야 합니다. 예:

```
report.CRITICAL: LogicException: Property "Street." does not have accessor method "getStreet." in class "Magento\Quote\Api\Data\AddressInterface". in vendor/magento/framework/Reflection/NameFinder.php:103
```

<u>실제 결과</u>:

끝점이 잘못된 매개 변수의 유효성을 검사하지 않고 `500 status code` 오류를 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
