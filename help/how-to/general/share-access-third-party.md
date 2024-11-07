---
title: 클라우드 인프라의 Adobe Commerce에 대한 서드파티 테스트 팁
description: 이 문서에서는 클라우드 인프라에서 Adobe Commerce용 확장에 문제가 있을 때 테스트/유효성 검사를 위해 서드파티와 액세스를 공유하는 옵션을 제공합니다.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에 대한 서드파티 테스트 팁

이 문서에서는 클라우드 인프라에서 Adobe Commerce용 확장에 문제가 있을 때 테스트/유효성 검사를 위해 서드파티와 액세스를 공유하는 옵션을 제공합니다.
서드파티에 액세스할 수 있는 방법을 결정할 때는 적절한 내부 데이터 보안 절차 및 요구 사항을 따라야 합니다.

## 영향을 받는 제품 및 버전:

* 클라우드 인프라의 Adobe Commerce 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## 테스트에 사용할 환경

내부 보안 표준에 따라 로컬 환경에서 서드파티 문제 해결을 선택할 수 있습니다. 문제를 로컬에서 재현할 수 없는 경우 클라우드 환경에 대한 액세스를 제공할 수 있습니다. 그렇게 하기로 선택한 경우 내부 보안 표준 내에서 작업하십시오. 클라우드 환경에 대한 액세스를 제공하는 경우 서드파티에서 수행할 수 있는 작업과 복제만 하거나 코드 변경 허용과 같은 작업에 필요한 승인이 무엇인지 명확히 해야 합니다. 이는 프로덕션 환경에 특히 중요합니다.

## 서드파티에게 액세스 및 데이터 제공

* 클라우드 환경에 대한 서드파티 공급업체 액세스 권한을 제공합니다. 관련 문서:

   * [Adobe Commerce 도움말 센터 사용 안내서 > 공유 액세스: 다른 사용자가 귀하의 계정에 액세스할 수 있는 권한을 부여합니다](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access).
   * 사용 안내서에서 [Commerce 계정 공유](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-share).

* 데이터베이스 덤프를 만들거나 타사 공급업체에 이 작업을 수행할 수 있는 액세스 권한을 부여합니다. 이 작업은 CLI 를 사용하거나 Commerce 관리에서 수행할 수 있습니다. 이 DB 덤프는 고객 데이터를 난독화하므로 고유/고객 데이터가 없는 코드 및 제품 SKU 등이 제공됩니다. 참조용으로 지원 기술 자료에서 [Commerce 계정 공유](/help/how-to/general/create-database-dump-on-cloud.md)를 사용하십시오.
* 테스트가 완료되면 지원 기술 자료의 [Adobe Commerce 도움말 센터 사용 안내서 > 취소(공유 액세스 삭제)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access)에 설명된 대로 클라우드 환경에 대한 공유 액세스를 취소해야 합니다.

## 테스트 모범 사례

표준 방법은 로컬 환경에서 문제를 해결하는 것입니다. 문제를 로컬에서 재현할 수 없는 경우 스테이징으로 이동합니다. 타사에서 프로덕션을 확인해야 할 수도 있습니다. 서드파티는 프로덕션 및 스테이징에서 문제를 재현하고 코드를 변경하지 말아야 한다는 것을 인지하고 코드를 변경해야 하는 경우 먼저 사용자의 허가를 받아야 합니다.

## 관련 읽기

* 지원 기술 자료의 [Adobe Commerce에서 타사 확장을 사용하는 모범 사례](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento).
