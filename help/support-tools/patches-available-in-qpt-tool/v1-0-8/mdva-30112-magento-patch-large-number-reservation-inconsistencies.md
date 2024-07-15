---
title: 'MDVA-30112: 큰 숫자 예약 불일치'
description: MDVA-30112 패치는 'inventory_reservation' 테이블에 예기치 않게 많은 [reservation inconsistents](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies)가 있는 문제를 해결합니다. 예약 불일치에는 등록되지 않은 미등록 개설 주문과 등록되지 않은 완료 주문이 포함된다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112: 큰 숫자 예약 불일치

MDVA-30112 패치를 사용하면 `inventory_reservation` 테이블에서 예기치 않게 많은 [예약 불일치](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies)가 발생하는 문제가 해결됩니다. 예약 불일치에는 등록되지 않은 미등록 개설 주문과 등록되지 않은 완료 주문이 포함된다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[bunch-size](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) 값은 한 번에 로드할 주문 수에 대한 값입니다. 이 값보다 많은 주문이 있는 경우 Adobe Commerce은 보류 중인 상태의 주문이 불일치로 간주됩니다.

>[!NOTE]
>
>세 가지 다른 인벤토리 불일치 문제를 해결하는 패치 MDVA-33281이 있습니다. CLI에서 `bin/magento inventory:reservation:list-inconsistencies`을(를) 실행할 때 PHP에 치명적인 오류가 발생합니다. 또 다른 해결된 문제는 불일치 목록의 중복 데이터입니다. 또한 주문이 이루어지기 전에 예약이 생성되는 문제(주문이 이루어진 후 예약을 기준으로 한 이전 실현). 해결 방법은 지원 기술 자료에서 [MDVA-33281: 인벤토리 불일치 문제](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md)를 참조하세요.

<u>필수 구성 요소</u>:

CLI에서 다음 명령을 실행하여 `inventory_reservation` 테이블에 일치하지 않는 예약을 나열합니다.

```
magento inventory:reservation:list-inconsistencies
```

예기치 않게 많은 예약 불일치가 표시되고/되거나 명령이 완료되지 않습니다.

<u>재현 단계</u>:

1. CLI에서 다음 명령을 실행하여 불일치를 해결합니다.

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. 세 가지 주문:
   * 각 제품을 단일 로 할당합니다.
   * 주문 상태가 &quot;보류 중&quot;이 되도록 수표/금전 주문 결제 방법을 사용합니다.
1. `inventory_reservation` 테이블에 -1 수량의 레코드 세 개가 표시됩니다. CLI에서 다음 명령을 실행하여 불일치를 확인합니다.

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   이렇게 하면 결과가 반환되지 않습니다.

1. CLI에서 다음 명령을 실행합니다.

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   &quot;보류 중&quot; 상태 주문이 불일치로 표시됩니다.

1. CLI에서 다음 명령을 실행합니다.

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>예상 결과</u>:

Adobe Commerce은 &quot;보류 중&quot; 상태 주문의 불일치를 해결해서는 안 됩니다. &#39;완료&#39;, &#39;마감&#39; 및 &#39;취소됨&#39; 상태의 주문에 대해 불일치 항목이 해결되어야 합니다.

<u>실제 결과</u>:

지정된 bunch-size 값보다 많은 주문이 있는 경우 Adobe Commerce은 &quot;보류 중&quot; 상태의 주문을 불일치로 간주하고 동일한 주문에 대해 여러 불일치 해결 레코드를 추가합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
