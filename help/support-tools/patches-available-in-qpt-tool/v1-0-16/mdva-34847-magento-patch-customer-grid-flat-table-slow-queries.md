---
title: 'MDVA-34847: customer_grid_flat 테이블 느린 쿼리'
description: MDVA-34847 패치는 'customer_grid_flat' 테이블에서 느린 쿼리가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847: customer_grid_flat 테이블 느린 쿼리

MDVA-34847 패치는 `customer_grid_flat` 테이블에서 느린 쿼리가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.3

**Adobe 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`customer_grid_flat` 테이블에서 느린 쿼리가 발생합니다.

<u>재현 단계</u>:

1. 사용자 지정 범위의 관리자 사용자를 만듭니다(예: **GWS** = *0,* 설정 및 **ID** = *1*&#x200B;인 기존 기본 웹 사이트 선택).
1. 모든 제품 및 범주 항목을 만듭니다.
1. 프론트 엔드에서 주문하세요.
1. 새 사용자로 관리자에 로그인합니다.
1. 판매 표(**판매 > 주문**)로 이동합니다.
1. SQL 쿼리가 DB(데이터베이스)로 전송되었는지 확인합니다.

<u>예상 결과</u>:

관리자 GWS 확장은

```sql
int
```

값

```sql
website_id
```

예상대로 SQL 조건:

```sql
main_table.website_id IN (1)
```

<u>실제 결과</u>:

관리자 GWS 확장이 다음 조건을 추가했습니다.

```sql
website_id
```

값:

```sql
string
```

, 다음과 같음:

```sql
main_table.website_id IN ('1')
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
