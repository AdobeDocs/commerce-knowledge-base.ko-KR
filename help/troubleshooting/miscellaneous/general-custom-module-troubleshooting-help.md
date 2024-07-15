---
title: 일반 사용자 정의 모듈 문제 해결 도움말
description: 이 문서에서는 Adobe Commerce의 사용자 정의 모듈 문제를 해결하는 데 도움이 되는 일반 도구에 대해 설명합니다.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 일반 사용자 정의 모듈 문제 해결 도움말

이 문서에서는 Adobe Commerce의 사용자 정의 모듈 문제를 해결하는 데 도움이 되는 일반 도구에 대해 설명합니다.

## 문제

사용자 정의 모듈의 기능에 문제가 있고 문제를 나타내는 명백한 오류 메시지가 없는 경우 인스턴스의 로그를 확인해야 합니다.

## 솔루션

오류에 사용자 지정 모듈 이름을 사용하는 항목이 있는지 확인하려면 로그를 확인하십시오.  관련된 오류에 따라 솔루션이 저절로 표시되거나 [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)을 열려면 유용한 Adobe Commerce 로그 정보를 포함해야 할 수도 있습니다. 로그의 위치 및 가능한 솔루션에 대한 정보는 다음 단락을 참조하십시오.

### Adobe Commerce(모든 배포 메서드), Magento Open Source, 모든 2.X 버전

1. 로그 위치:
   * 지원 기술 자료의 [클라우드 인프라 시작 계획 아키텍처 로그에 대한 Adobe Commerce](/help/how-to/general/log-locations-directories-for-starter-plan.md).
   * 지원 기술 자료에서 [클라우드 인프라 Pro 계획 아키텍처 로그의 Adobe Commerce](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md).
1. 사용자 정의 모듈을 활성화, 비활성화 또는 제거하려면 발견된 오류에 따라 다음 문서에서 이러한 작업을 자세히 설명합니다.
   * 개발자 설명서에서 [모듈을 사용하거나 사용하지 않도록 설정](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html).
   * 개발자 설명서에서 [모듈 제거](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html).

### 클라우드 인프라의 Adobe Commerce, 모든 버전

1. 개발자 설명서에서 로그 위치: [클라우드 인프라 로그의 Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html).
1. 사용자 정의 모듈을 활성화, 비활성화 또는 제거하려면 발견된 오류에 따라 개발자 설명서의 다음 문서에서 이러한 작업에 대해 자세히 설명합니다.
   * [확장 설치, 관리 및 업그레이드](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [구성 요소 배포 실패](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## 관련 읽기

개발자 설명서에서:

* [모듈 개요](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [선택적 샘플 데이터를 설치하는 동안 오류가 발생했습니다](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [예외 처리](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [설치 중 예외](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [모듈 관리자 실행](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [모듈 구성 파일](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [메모리 부족 오류](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
