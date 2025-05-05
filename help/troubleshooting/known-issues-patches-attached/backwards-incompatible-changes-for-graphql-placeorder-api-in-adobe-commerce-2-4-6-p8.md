---
title: 'Adobe Commerce 2.4.6-p8의  [!DNL GraphQL] &grave;placeOrder&grave; [!DNL API] 에 대한 이전 버전과 호환되지 않는 변경 내용'
promoted: true
description: 이 문서에서는 이전 2.4.6 패치 버전에 표시된 대로 'placeOrder' [!DNL GraphQL API] 가 예상 오류 응답을 반환하지 않는 알려진 Adobe Commerce 버전 2.4.6-p8 Cloud 및 온-프레미스 문제에 대한 패치를 제공합니다. 이로 인해 PWA 상점 또는 다른  [!DNL GraphQL API] 기반 상점을 사용하는 상인의 체크아웃 환경이 손상될 수 있습니다.
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Adobe Commerce 2.4.6-p8의 [!DNL GraphQL] `placeOrder` [!DNL API]에 대해 이전 버전과 호환되지 않는 변경 내용

이 문서에서는 `placeOrder` [!DNL GraphQL API]이(가) 이전 2.4.6 패치 버전에 표시된 대로 예상 오류 응답을 반환하지 않는 알려진 Adobe Commerce 버전 2.4.6-p8 Cloud 및 온-프레미스 문제에 대한 패치를 제공합니다. 이로 인해 상점을 위해 [!DNL PWA] 상점 또는 다른 [!DNL GraphQL API] 기반 상점 등을 사용하는 상인의 체크아웃 환경이 손상될 수 있습니다.

>[!NOTE]
>
>패치를 적용하는 데 문제가 있는 경우 지원 서비스에 문의하십시오.

## 영향을 받는 제품 및 버전

* Cloud 2.4.6-p8의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.4.6-p8

## 문제

Adobe Commerce 2.4.6-p8 보안 전용 패치로 업그레이드한 후 [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)이(가) 이전 2.4.6 패치 버전에 표시된 대로 예상 오류 응답을 반환하지 않습니다. 이로 인해 상점을 위해 [!DNL PWA] 상점 또는 다른 [!DNL GraphQL API] 기반 상점 등을 사용하는 상인의 체크아웃 환경이 손상될 수 있습니다.

<u>재현할 단계</u>:

오류 응답이 예상되는 `placeOrder` [!DNL GraphQL] 요청을 실행합니다.

<u>예상 결과</u>:

예상 오류 응답을 받습니다.

<u>실제 결과</u>:

예상된 오류 응답 대신 다음과 같은 새 `errors` 키가 있는 성공적인 응답을 받게 됩니다.

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## Adobe Commerce on Cloud 및 Adobe Commerce 온프레미스 소프트웨어 솔루션

문제를 해결하려면 패치를 적용합니다.
다운로드하려면 다음 링크를 클릭하십시오.

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## 패치 적용 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)을 참조하십시오.

## Adobe Commerce on Cloud 판매자의 경우에만 - 패치가 적용되었는지 여부를 확인하는 방법

문제가 패치되었는지 쉽게 확인할 수 없는 점을 고려하면 패치가 성공적으로 적용되었는지 확인할 수 있습니다.

<u>샘플 파일 `VULN-27015-2.4.7_COMPOSER.patch` **을(를) 예로 사용하여 다음 단계를 수행하여 이 작업을 수행할 수 있습니다</u>**:

1. [설치 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. 명령 실행: <br>
   ![ac-13283-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 다음과 유사한 출력이 표시되어야 합니다. 여기서 VULN-27015은 *적용됨* 상태를 반환합니다.

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

