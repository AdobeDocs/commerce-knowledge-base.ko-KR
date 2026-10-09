---
title: 제품이 상점 앞에 표시되지 않음
description: 이 문서에서는 제품이 상점 앞에 표시되지 않는 경우에 대한 해결 방법을 제공합니다.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%
---
# 제품이 상점 앞에 표시되지 않음

이 문서에서는 제품이 상점 앞에 표시되지 않는 경우에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 X.X.X
* 클라우드 인프라의 Adobe Commerce X.X.X

## 문제

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다.
1. **카탈로그** > **제품**(으)로 이동합니다.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. **제품 추가**&#x200B;를 클릭하고 제품 만들기 프로세스를 진행합니다. 또는 CSV 파일에서 제품을 가져옵니다.

<u>예상 결과</u>:

상품은 매장에 진열되어 있습니다.

<u>실제 결과</u>:

제품이 표시되지 않습니다.

## 원인

이는 여러 가지 이유로 인해 발생할 수 있습니다. 아래 단계에 따라 문제를 식별하고 해결하는 데 도움이 될 수 있는 주요 사항을 확인하십시오.

## 솔루션

다음 각 사항에서 이 문제를 해결할 수 있습니다.

* 관리에서 제품 설정을 확인하십시오. **카탈로그** > **제품**(으)로 이동하여 제품 페이지를 열고 다음 필드가 올바르게 구성되었는지 확인하십시오.
  * **제품 사용** = *예.*
  * **재고 상태**: *재고*. 또는 *재고 부족*&#x200B;이 올바른 값이면 **재고 부족 제품 표시**(**스토어** > **설정** > **구성** > **카탈로그** > **재고** > **재고 옵션** > **재고 부족 제품 표시**)가 *예*(전역 수준에서 구성됨)로 설정되어 있는지 확인하십시오.
  * **범주**: 범주 페이지에서 제품을 찾으려고 하는 경우 제품이 범주에 할당되었는지 확인하십시오. 문제 해결을 단순화하려면 현재 페이지에서 새 카테고리를 만들고 제품을 할당합니다.
  * **가시성** = *카탈로그, 검색*
  * **웹 사이트의 제품** 섹션에서 제품이 올바른 웹 사이트에 할당되었는지 확인하십시오.
  * 범위 선택기를 상점 전면에서 제품을 찾으려는 상점 보기로 전환한 다음 동일한 설정을 확인합니다.
* 콘솔에서 `bin/magento indexer:reindex`을(를) 실행하여 전체 리인덱싱을 수행하고 **시스템** > **도구** > **캐시 관리**&#x200B;에서 관리자의 모든 캐시를 플러시하거나 `bin/magento cache:clean`을(를) 실행하여 콘솔에서 모든 캐시를 플러시합니다.
* 위의 사항이 도움이 되지 않으면 `var/log` 디렉터리의 로그를 확인하여 추가 조사를 시작할 수 있습니다.



