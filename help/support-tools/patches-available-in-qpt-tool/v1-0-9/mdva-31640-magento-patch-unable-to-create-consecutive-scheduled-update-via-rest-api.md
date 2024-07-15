---
title: 'MDVA-31640 패치: REST API를 통해 연속적인 예약된 업데이트를 만들 수 없음'
description: MDVA-31640 패치는 업데이트 시작 날짜가 이전의 기존 업데이트 종료 날짜와 일치하는 경우 REST API를 사용하여 여러 스토어에 대해 특별 가격에 대한 새 예약 업데이트를 만들 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-31640 패치: REST API를 통해 연속적인 예약된 업데이트를 만들 수 없음

MDVA-31640 패치는 업데이트 시작 날짜가 이전의 기존 업데이트 종료 날짜와 일치하는 경우 REST API를 사용하여 여러 스토어에 대해 특별 가격에 대한 새 예약 업데이트를 만들 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치를 만들었습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온 클라우드 인프라 및 Adobe Commerce 온-프레미스 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

업데이트 시작 날짜가 이전의 기존 업데이트 종료 날짜와 일치하는 경우 REST API를 사용하여 여러 스토어에 대해 특가에 대한 새 예약 업데이트를 만들 수 없는 문제를 해결했습니다.

<u>재현 단계</u>:

1. 추가 웹 사이트, 스토어 및 스토어 보기를 설정합니다.
1. 간단한 두 가지 제품인 &quot;product1&quot;과 &quot;product2&quot;를 만듭니다.
1. 한 웹 사이트에 product1을 할당하고 두 웹 사이트 모두에 product2를 할당합니다.
1. ID 1인 스토어의 스토어 보기에서 제품1의 특별 가격에 대해 예약된 업데이트를 만듭니다. 다음 페이로드와 함께 `rest/V1/products/special-price`에 대한 REST API `POST` 요청 사용:
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. 다음 페이로드를 사용하여 `rest/V1/products/special-price`에 대한 REST API `POST` 요청을 사용하여 ID 1 및 2의 스토어에 대한 두 스토어 보기에서 제품2의 특별 가격에 대한 예약된 업데이트를 만듭니다(`price_from` 날짜는 이전 요청의 `price_to` 날짜와 동일함).
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>예상 결과</u>:

두 스토어 조회수 모두에 특별 가격 변경으로 예약된 업데이트가 생성됩니다.

<u>실제 결과</u>:

Adobe Commerce에 오류가 발생합니다. 예약된 업데이트가 생성되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
