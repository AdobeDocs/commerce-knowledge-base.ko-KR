---
title: 'ACSD-53845: 소비자 max_messages = 0일 때 MySQL 연결 시간 초과 문제'
description: ACSD-53845 패치를 적용하여 소비자 'max_messages = 0' 시 MySQL 연결 시간이 초과되는 Adobe Commerce 문제를 수정합니다.
feature: REST, Configuration
role: Admin, Developer
exl-id: 68f862ed-5401-41e9-a6cc-cef44ebc1915
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-53845: 소비자 `max_messages = 0`에서 MySQL 연결 시간 초과 문제 발생

ACSD-53845 패치는 소비자 `max_messages = 0`에서 MySQL 연결 시간이 초과되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-53845입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

소비자 `max_messages = 0`에서 MySQL 연결 시간이 초과됩니다.

그러나 트랜잭션을 시작하면 데이터베이스에 대한 연결이 복원됩니다.

<u>재현 단계</u>:

1. `async/bulk/V1/products` REST API 끝점을 사용하여 제품을 대량 업데이트하도록 요청을 보냅니다.
1. `magento_operation` 테이블에서 상태를 확인합니다.

<u>예상 결과</u>:

제품이 업데이트됩니다.

<u>실제 결과</u>:

1. 오류가 기록됩니다.

   ```
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. 이 작업의 *상태*&#x200B;이(가) `magento_operation` 테이블에 *4* 상태로 남아 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
