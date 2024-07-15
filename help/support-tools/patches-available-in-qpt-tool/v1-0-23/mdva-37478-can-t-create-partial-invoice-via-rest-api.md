---
title: "MDVA-37478: REST API를 통해 부분 송장을 만들 수 없음"
description: MDVA-37478 패치는 결제 방법**계정입금**이 적용된 주문에 대해 REST API를 통해 부분 송장을 생성할 수 없는 경우 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37478입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478: REST API를 통해 부분 송장을 만들 수 없음

MDVA-37478 패치는 결제 방법 **계정에 대한 결제**(으)로 주문된 주문에 대해 REST API를 통해 부분 송장을 만들 수 없는 경우 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37478입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.3-p1의 Adobe Commerce용으로 설계되었습니다
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.3.7과도 호환됩니다

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소</u>:

B2B 모듈이 설치된 Adobe Commerce

<u>재현 단계</u>:

1. **B2B 회사**&#x200B;를 사용하도록 설정합니다.
1. **계정에서 결제** 결제 방법을 사용하도록 설정합니다.
1. 2개의 간단한 제품을 만듭니다.
1. 회사 계정을 만듭니다.
1. 생성된 2개 제품의 총 가격을 초과하는 회사 크레딧을 추가합니다.
1. 생성된 회사 계정을 사용하여 프론트엔드에 로그인합니다.
1. 장바구니에 만든 2개 제품을 추가하고 **계정에서 결제** 결제 방법을 사용하여 체크아웃합니다.
1. REST API를 통해 생성된 주문에 대한 부분 송장을 생성해 보십시오.

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>예상 결과</u>:

예상대로 **계정 결제** 결제 방법을 사용하여 수행한 주문에 대해 부분 송장이 만들어집니다.

<u>실제 결과</u>:

REST API에서 다음 오류가 반환됩니다.

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
