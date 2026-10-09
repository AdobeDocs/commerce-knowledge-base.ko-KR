---
title: 'ERROR: 클라우드 인프라의 Adobe Commerce에서 준비에 실패했습니다.'
description: 이 문서에서는 페이지 캐시가 준비되고 오류와 함께 실패하는 경우에 대한 솔루션을 제공합니다.
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%
---
# ERROR: 클라우드 인프라의 Adobe Commerce에서 준비에 실패했습니다.

이 문서에서는 페이지 캐시가 준비되고 오류와 함께 실패하는 경우에 대한 솔루션을 제공합니다.

*오류: 준비 중 실패:`<website link>`*

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

캐시 준비 실패.

<u>재현 단계</u>:

캐시 준비 작업을 시작합니다.

<u>예상 결과</u>:

페이지 또는 전체 사이트가 로드됩니다.

<u>실제 결과</u>:

사이트를 사용할 수 없거나 응답 시간이 너무 깁니다. *오류: 준비 중 실패:`<website link>`*

## 원인

HTTP 액세스 제어를 사용하도록 설정한 경우 캐시 미리 보기가 작동하지 않습니다.

## 솔루션

액세스 제어를 사용할 수 없는지 확인합니다. 특정 분기/환경으로 이동하여 **설정** 아이콘을 클릭하고 **HTTP 액세스 제어** 설정을 확인합니다. 이 시나리오에서는 캐시 웜업을 수행할 수 없으며 액세스 제어를 사용하지 않도록 설정해야 합니다.

## 관련 읽기

* 사용 안내서의 [Adobe Commerce 사용 안내서 > 전체 페이지 캐시](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching).
* 지원 기술 자료의 [Adobe Commerce에서 캐시 준비 및 사이트를 사용할 수 없음](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md).
