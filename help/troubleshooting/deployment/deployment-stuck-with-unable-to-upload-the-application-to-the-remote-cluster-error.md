---
title: '"원격 클러스터에 응용 프로그램을 업로드할 수 없음" 오류가 발생하여 배포가 중단됨'
description: '이 문서는 배포가 중단되는 Adobe Commerce 문제에 대한 솔루션을 제공하며 다음 오류 메시지는 배포 로그에서 확인할 수 있습니다. *"오류: 원격 클러스터에 애플리케이션을 업로드할 수 없음"*.'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# &quot;원격 클러스터에 응용 프로그램을 업로드할 수 없음&quot; 오류가 발생하여 배포가 중단됨

이 문서에서는 배포가 중단되는 Adobe Commerce 문제에 대한 솔루션을 제공합니다. 배포 로그에서 다음 오류 메시지를 찾을 수 있습니다. *&quot;오류: 응용 프로그램을 원격 클러스터&quot;*&#x200B;에 업로드할 수 없습니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

<u>재현 단계</u>:

수동으로 또는 환경의 병합, 푸시 또는 동기화를 수행하여 배포를 트리거합니다.

<u>예상 결과</u>:

배포가 완료되었습니다.

<u>실제 결과</u>:

배포가 중단되고 클라우드 UI의 배포 오류 로그에 다음 오류 메시지가 표시됩니다. *&quot;오류: 응용 프로그램을 원격 클러스터에 업로드할 수 없음&quot; 배포 실패 후 배포 로그에 있는 경우 사이트에 &quot;503 첫 번째 바이트 시간 초과&quot;* 오류가 표시될 수 있습니다.

## 원인

이 문제는 사용 가능한 스토리지가 중단되어 발생합니다.

## 솔루션

로그 디렉토리를 정리하거나 디스크 공간을 늘릴 수 있습니다.

정리할 디렉토리는 다음과 같습니다.

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Adobe Commerce on cloud infrastructure 스타터 계획 아키텍처를 사용하는 경우 디스크 공간을 늘리는 방법에 대한 자세한 내용은 지원 기술 자료에서 [클라우드의 통합 환경을 위한 디스크 공간 늘리기](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)를 참조하십시오. 동일한 지침을 사용하여 클라우드 인프라 Pro 계획 아키텍처 통합 환경에서 Adobe Commerce의 공간을 늘릴 수 있습니다. Pro Production/Staging의 경우 [Adobe Commerce 지원 티켓을 파일링](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket)하고 증가된 디스크 공간을 요청해야 합니다. 그러나 Adobe Commerce이 사용자를 위해 이러한 매개 변수를 모니터링하고 계약에 따라 경고 및/또는 작업을 수행하므로 일반적으로 Pro 플랜의 스테이징/프로덕션에서 이 문제를 처리할 필요가 없습니다.
