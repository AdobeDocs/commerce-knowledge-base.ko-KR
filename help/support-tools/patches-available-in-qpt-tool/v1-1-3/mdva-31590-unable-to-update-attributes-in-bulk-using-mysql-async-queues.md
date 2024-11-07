---
title: 'MDVA-31590: MySQL 비동기 큐를 사용하여 특성을 일괄적으로 업데이트할 수 없음'
description: MDVA-31590 패치는 사용자가 MySQL 비동기 큐를 사용하여 속성을 일괄적으로 업데이트할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-31590입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590: MySQL 비동기 큐를 사용하여 특성을 일괄적으로 업데이트할 수 없습니다.

MDVA-31590 패치는 사용자가 MySQL 비동기 큐를 사용하여 속성을 일괄적으로 업데이트할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-31590입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 메서드) 2.4.0

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0-2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 MySQL 비동기를 사용하여 속성을 일괄적으로 업데이트할 수 없습니다.

<u>재현 단계</u>:

1. 백엔드의 제품 그리드에서 대량 작업을 수행하여 일부 제품에 대한 속성 값을 업데이트합니다.
   * 제품을 확인하고 작업 드롭다운에서 **특성 업데이트**&#x200B;를 선택합니다.
1. 필요한 속성에 대한 값을 설정하고 웹 사이트에 제품을 할당하고 저장합니다.
1. 페이지가 다시 로드되면 다음과 같은 메시지가 표시됩니다.
   *작업 &quot;N개 선택한 제품에 대한 특성 업데이트&quot;: 1개 항목이 업데이트에 예약되었습니다.*
1. 몇 초 정도 기다린 후 백엔드 페이지를 다시 로드합니다.

<u>예상 결과</u>:

1. 페이지에 다음과 같은 업데이트 메시지가 표시됩니다. *1개 항목이 업데이트되었습니다.*
1. 관련 제품의 속성 값이 업데이트됩니다.
1. DB에서 `magento_bulk` 테이블 및 `magento_operation` 테이블(대량 관련 작업) 모두에 새 레코드가 만들어집니다.
1. 큐 `product_action_attribute.update` 및/또는 `product_action_attribute.website.update`과(와) 관련된 `queue_message` 테이블에 새 레코드가 만들어졌습니다.
1. `queue_message_status` 테이블에 상태가 &quot;4&quot;인 레코드가 있습니다.
1. `system.log`에 오류가 없습니다.

<u>실제 결과</u>:

1. 페이지에 다음과 같은 메시지가 계속 표시됩니다.
   *작업 &quot;N개 선택한 제품에 대한 특성 업데이트&quot;: 1개 항목이 업데이트에 예약되었습니다.*
1. 제품에 대한 속성 값이 업데이트됩니다.
1. `message_bulk` 테이블에 새 레코드가 만들어졌지만 `magento_operation` 테이블에 관련 레코드가 없습니다.
1. `queue_message` 및 `queue_message_status` 테이블에 새 레코드가 만들어집니다.
1. `queue_message_status` 테이블에 오류 상태의 레코드가 있습니다(상태 값 &quot;6&quot;).
1. `system.log`에 다음과 유사한 오류가 있습니다.
   *main.CRITICAL: 메시지가 거부되었습니다. SQLSTATE[23000]: 무결성 제약 조건 위반: 1048 열 &#39;operation_key&#39;는 null일 수 없습니다. 쿼리는 INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) 값(?, ?, ?, ?, ?, ?, ?) [][]*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
