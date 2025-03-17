---
title: '"프로젝트 빌드 오류: 빌드 후크가 상태 코드 1로 실패"로 인해 배포가 실패합니다.'
description: '이 문서에서는 배포 프로세스의 빌드 단계가 실패하는 Adobe Commerce on cloud infrastructure 문제의 원인 및 솔루션에 대해 알아보고 오류 메시지를 요약하여 *"Error building project: The build hook failed with status code 1"*로 설명합니다.'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 6a880a57c6cafb34fa51706f7bab1e23310bcef7
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# &quot;프로젝트 빌드 오류: 빌드 후크가 상태 코드 1로 실패&quot;로 인해 배포가 실패합니다.

이 문서에서는 배포 프로세스의 빌드 단계가 실패하는 Adobe Commerce on cloud infrastructure 문제의 원인과 솔루션에 대해 알아보고 오류 메시지를 요약합니다. *&quot;프로젝트 빌드 오류: 빌드 후크가 상태 코드 1&quot;*.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

<u>재현 단계</u>:

수동으로 또는 환경의 병합, 푸시 또는 동기화를 수행하여 배포를 트리거합니다.

<u>예상 결과</u>:

배포가 완료되었습니다.

<u>실제 결과</u>:

1. 빌드 단계가 실패하고 전체 배포 프로세스가 중단됩니다.
1. 배포 오류 로그에서 오류 메시지는 다음으로 끝납니다. *&quot;프로젝트 빌드 오류: 빌드 후크가 상태 코드 1로 실패했습니다. 빌드가 중단되었습니다.*

## 원인

환경 구축이 실패한 이유는 여러 가지가 있습니다. 일반적으로 배포 로그에 긴 오류 메시지가 표시됩니다. 첫 번째 부분은 이유에 대해 더 구체적이고 결론은 *입니다.&quot;프로젝트 빌드 오류: 빌드 후크가 상태 코드 1로 실패했습니다. 빌드가 중단되었습니다.*

첫 번째 문제별 부분을 자세히 살펴보면 문제를 식별하는 데 도움이 될 것입니다. 다음은 가장 일반적인 사례이며 다음 섹션에서는 이러한 사례에 대한 솔루션을 제공합니다.

* 사용 가능한 저장 공간이 없습니다.
* 잘못된 ECE-Tools 구성.
* 적용하려는 패치가 Adobe Commerce 버전과 호환되지 않거나 적용된 다른 패치 또는 사용자 지정과 충돌합니다.
* 사용자 지정 모듈 코드의 문제로 인해 빌드가 실행되지 않습니다.

## 솔루션

* 저장 공간이 충분한지 확인합니다. 사용 가능한 공간을 확인하는 방법에 대한 자세한 내용은 [CLI를 사용하여 클라우드 환경에서 디스크 공간 확인](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md) 문서를 참조하십시오. 로그 디렉토리를 정리하거나 디스크 공간을 늘릴 수 있습니다.
* ECE-Tools가 올바로 구성되어 있는지 확인합니다.
* 문제를 일으키는 것이 패치인지 확인합니다. 충돌을 해결하거나 [Adobe Commerce 지원](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)에 문의하십시오. 자세한 내용은 아래를 참조하십시오.
* 문제를 일으키는 것이 사용자 정의 확장인지 확인합니다. 충돌을 해결하거나 확장 개발자에게 문의하여 솔루션을 확인하십시오.

다음 단락에서는 자세한 내용을 제공합니다.

### 로그 정리 및/또는 공간 늘리기

정리할 디렉터리:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Adobe Commerce on cloud infrastructure 스타터 계획 아키텍처를 사용하는 경우 디스크 공간을 늘리는 방법에 대한 자세한 내용은 [클라우드의 통합 환경을 위한 디스크 공간 늘리기](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)를 참조하십시오. 클라우드 인프라 Pro 계획 아키텍처 통합 환경에서 Adobe Commerce의 공간을 늘리는 데에도 동일한 지침을 사용할 수 있습니다. Pro Production/Staging의 경우 [Adobe Commerce 지원](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)에 티켓을 제출하고 디스크 공간 증가를 요청해야 합니다. 그러나 플랫폼에 의해 모니터링됩니다. 하지만 Adobe Commerce이 이러한 매개 변수를 모니터링하고 경고하거나 계약에 따라 작업을 수행하므로 일반적으로 Pro 아키텍처의 스테이징/프로덕션에서 이 문제를 처리할 필요가 없습니다.

### ECE-tools 가 올바르게 구성되었는지 확인

1. 빌드 후크가 `magento.app.yaml` 파일에 올바르게 정의되어 있는지 확인하십시오. Adobe Commerce 2.2.X를 사용하는 경우 빌드 후크를 다음과 같이 정의해야 합니다.

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   [ece-tools로 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) 문서를 참조하십시오.

1. 다음 명령을 실행하여 ECE-tools 패키지가 `composer.lock` 파일에 있는지 확인하십시오.

   ```bash
   grep '"name": "magento/ece-tools"' composer.lock
   ```

   지정된 경우 응답은 다음 예제와 같습니다.

   ```bash
   "name": "magento/ece-tools", "version": "2002.0.20",
   ```

참조하려면 [ece-tools로 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) 문서를 참조하십시오.

### 패치 때문에 문제가 발생한 건가요?

적용된 패치로 인해 환경이 성공적으로 빌드되지 않는 경우 배포 로그에 다음과 유사한 메시지가 표시됩니다.

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

이러한 오류 메시지는 적용하려는 패치가 다른 Adobe Commerce 버전에서 만들었거나 사용자 정의 또는 이전에 적용한 패치와 충돌했음을 의미합니다. 충돌을 해결하거나 [Adobe Commerce 지원](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)에 문의하십시오.

### 확장 때문에 문제가 발생합니까?

환경을 성공적으로 빌드하지 못하는 것이 사용자 지정 확장인 경우 이 모듈로 인해 발생하는 특정 충돌과 함께 배포 로그에 언급된 사용자 지정 모듈 이름이 표시됩니다. 충돌을 해결하거나 확장 개발자에게 문의하여 솔루션을 확인하십시오.

### 변경 사항이 적용되었는지 확인합니다.

변경 사항을 커밋하고 푸시합니다. 이렇게 하면 배포가 자동으로 트리거됩니다.
