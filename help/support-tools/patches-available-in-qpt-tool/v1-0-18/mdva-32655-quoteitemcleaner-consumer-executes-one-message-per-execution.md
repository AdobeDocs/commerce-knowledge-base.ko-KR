---
title: 'MDVA-32655: "quoteItemCleaner" 소비자가 실행당 하나의 메시지를 실행합니다.'
description: MDVA-32655 패치는 여러 제품을 삭제한 후 소비자 'quoteItemCleaner'에 대한 잘못된 "진행 중" 메시지 상태를 올바른 "완료" 메시지로 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우 사용할 수 있습니다. 패치 ID가 32655. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: &quot;quoteItemCleaner&quot; 소비자는 실행당 하나의 메시지를 실행합니다.

MDVA-32655 패치는 여러 제품을 삭제한 후 잘못된 &quot;진행 중&quot; 메시지 상태를 소비자 `quoteItemCleaner`에 대한 올바른 &quot;완료&quot; 메시지로 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우에 사용할 수 있습니다. 패치 ID가 32655. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.3

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`quoteItemCleaner` 소비자는 각 실행 시 하나의 메시지만 실행합니다.

<u>재현 단계</u>:

1. `queue_message_status` 데이터베이스 테이블을 확인하고 기존의 모든 큐 메시지가 &quot;완료&quot; 상태(상태 ID 4)인지 확인하십시오.
1. 자동 Adobe Commerce cron 실행을 중지합니다.
1. 두 개 또는 세 개의 간단한 제품을 만듭니다.
1. 이 세 가지 간단한 제품을 대량으로 삭제합니다.
1. `queue_message_status` 표에 상태 ID 2(새 레코드)의 `catalog_product_removed_queue` 주제에 대한 새 레코드가 3개 있습니다.
1. 다음 명령을 실행하여 보류 중인 `catalog_product_removed_queue`개의 메시지를 처리합니다.

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>예상 결과</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

`catalog_product_removed_queue` 메시지 상태가 모두 완료되도록 업데이트됩니다(ID=4).

<u>실제 결과</u>:

셋 중 하나의 레코드만 &quot;완료&quot; 상태로 업데이트됩니다(ID = 4). 다른 두 메시지의 상태는 상태 ID = 3(진행 중)입니다. 처리되지 않은 대기열 메시지가 있는 백로그가 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
