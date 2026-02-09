---
title: 일반 사용자 정의 모듈 문제 해결 도움말
description: 이 문서에서는 Adobe Commerce의 사용자 정의 모듈 문제를 해결하는 데 도움이 되는 일반 도구에 대해 설명합니다.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: d7c714cf5b2f9db139440d814af26c12001bb4d9
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# 일반 사용자 정의 모듈 문제 해결 도움말

이 문서에서는 Adobe Commerce의 사용자 정의 모듈 문제를 해결하는 데 도움이 되는 일반 도구에 대해 설명합니다.

## 문제

사용자 정의 모듈의 기능에 문제가 있고 문제를 나타내는 명백한 오류 메시지가 없는 경우 인스턴스의 로그를 확인해야 합니다.

## 솔루션

오류에 사용자 지정 모듈 이름을 사용하는 항목이 있는지 확인하려면 로그를 확인하십시오.  관련된 오류에 따라 솔루션이 저절로 표시되거나 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 열려면 유용한 Adobe Commerce 로그 정보를 포함해야 할 수도 있습니다. 로그의 위치 및 가능한 솔루션에 대한 정보는 다음 단락을 참조하십시오.

### Adobe Commerce(모든 배포 메서드), Magento Open Source, 모든 2.X 버전

1. 로그 위치는 지원 기술 자료의 [클라우드 인프라 Pro 계획 아키텍처 로그의 Adobe Commerce](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)에 있습니다.
1. 사용자 정의 모듈을 활성화, 비활성화 또는 제거하려면 발견된 오류에 따라 다음 문서에서 이러한 작업을 자세히 설명합니다.
   * 개발자 설명서에서 [모듈을 사용하거나 사용하지 않도록 설정](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/manage-modules).
   * 개발자 설명서에서 [모듈 제거](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

### 클라우드 인프라의 Adobe Commerce, 모든 버전

1. 개발자 설명서에서 로그 위치: [클라우드 인프라 로그의 Adobe Commerce](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/test/log-locations).
1. 사용자 정의 모듈을 활성화, 비활성화 또는 제거하려면 발견된 오류에 따라 개발자 설명서의 다음 문서에서 이러한 작업에 대해 자세히 설명합니다.
   * [확장 설치, 관리 및 업그레이드](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [구성 요소 배포 실패](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## 관련 읽기

개발자 설명서에서:

* [모듈 개요](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [선택적 샘플 데이터를 설치하는 동안 오류가 발생했습니다](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [예외 처리](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [설치 중 예외](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [모듈 관리자 실행](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [모듈 구성 파일](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/files/module-files)
* [메모리 부족 오류](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
