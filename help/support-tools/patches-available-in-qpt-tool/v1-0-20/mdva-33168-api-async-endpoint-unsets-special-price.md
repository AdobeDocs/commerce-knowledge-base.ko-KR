---
title: 'MDVA-33168: API 비동기 끝점이 특수 가격을 설정 해제합니다.'
description: MDVA-33168 패치는 API 비동기 끝점을 사용하여 제품 특성을 업데이트하면 특수 가격이 설정 해제되는 문제를 해결합니다.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168: API 비동기 끝점이 특별 가격을 설정 해제합니다.

MDVA-33168 패치는 API 비동기 끝점을 사용하여 제품 특성을 업데이트하면 특수 가격이 설정 해제되는 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-33168입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.3-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.3 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 스토어를 사용하여 웹 사이트 두 개를 만듭니다.
1. **스토어 > 구성 > 카탈로그 > 가격 > 카탈로그**(으)로 이동하여 **가격 범위** = *웹 사이트*&#x200B;를 설정합니다.
1. *text-type* 제품 특성을 만듭니다. 모든 옵션을 기본값으로 둡니다.
1. 작성된 속성을 기본 속성 세트에 추가합니다.
1. 번들 제품에 사용할 간단한 제품을 만듭니다.
1. 다음 예제 옵션을 사용하여 번들 제품을 만듭니다.
   * **제품 사용** = *예*.
   * **특성 집합** = *기본값*.
   * **제품 이름** = *번들-1*.
   * **SKU** = *번들-1*.
   * **동적 SKU** = *예*.
   * **가격** = *$100.00*.
   * **세금 등급** = *과세 대상 상품*.
   * **재고 상태** = *재고*.
1. **번들 항목**&#x200B;에서 다음 예제 옵션을 설정합니다.
   * **번들 항목 배달** = *함께*.
   * **옵션 제목** = *테스트*, **입력 유형** = *라디오 단추*, **필수** 확인란 = *선택됨*.
   * **기본값입니다** 확인란 = *선택되지 않음*.
   * **이름** = *단순-100*.
   * **SKU** = *simple-100*.
   * **가격** = *100.00*.
   * **가격 유형** = *고정*.
   * **기본 수량** = *1*.
   * **사용자 정의** 확인란 = *선택되지 않음*.
1. 범위를 기본이 아닌 상점으로 전환하고 특별 가격을 설정합니다. (예: **고급 가격 책정** 페이지에서 **특별 가격** = *4%* 및 **가격 보기** = *가격 범위*&#x200B;를 설정합니다.)
1. 다음 예제와 같이 기본값이 아닌 저장소 범위에서만 새 속성을 업데이트합니다.

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>예상 결과</u>:

다른 속성 값은 비동기 rest API를 사용하여 제품 속성을 업데이트할 때 예상대로 동일하게 유지됩니다.

<u>실제 결과</u>:

스토어 범위에서 비동기 rest API를 사용하여 설정한 특별 가격이 제거됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
