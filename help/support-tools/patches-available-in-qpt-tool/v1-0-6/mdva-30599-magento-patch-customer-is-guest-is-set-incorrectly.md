---
title: 'MDVA-30599: customer_is_guest가 잘못 설정되었습니다.'
description: MDVA-30599 패치는 API를 사용하여 만든 게스트 견적이 로그인한 고객에 대한 견적으로 잘못 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우 사용할 수 있습니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599: customer_is_guest가 잘못 설정되었습니다.

MDVA-30599 패치는 API를 사용하여 만든 게스트 견적이 로그인한 고객에 대한 견적으로 잘못 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우에 사용할 수 있습니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.4 - 2.4.0

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

API를 사용하여 만든 게스트 견적이 로그인한 고객에 대한 견적으로 잘못 표시됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 상점 첫 화면에서 장바구니에 제품을 게스트 사용자로 추가합니다.
1. Adobe Commerce DB에서 해당 `quote_id_mask`을(를) 찾습니다.
1. API 요청을 게스트 카트의 `quoteGuestCartRepositoryV1` 카트 저장소 인터페이스로 보냅니다. Swagger 또는 cURL 요청을 통해 수행할 수 있습니다.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>예상 결과</u>:

이에 대한 응답으로 `"customer_is_guest": true`을(를) 받습니다.

<u>실제 결과</u>:

이에 대한 응답으로 `"customer_is_guest": false`을(를) 받습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 패치 설치 후 추가 단계 필요

이 패치는 모든 새 손님용 카트에 효과적입니다. 기존 게스트 카트를 해결해야 하는 경우 `quote.customer_id`이(가) NULL인 레코드에 대해 `quote.customer_is_guest = 1`을(를) 설정하십시오. 다음과 유사한 쿼리를 실행할 수 있습니다.

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>프로덕션 환경에서 실행하기 전에 스테이징/통합 환경에서 쿼리를 테스트하는 것이 좋습니다. 또한 DB를 조작하기 전에 최근 백업을 수행하는 것이 좋습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
