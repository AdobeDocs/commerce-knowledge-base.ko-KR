---
title: 통합 환경 개선 요청 - Pro 및 Starter
description: Adobe Commerce on cloud infrastructure Pro 계획 아키텍처 고객이고 현재 표준 크기의 통합 환경을 사용하는 경우 또는 Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 고객이고 현재 표준 크기의 스테이징 환경을 사용하는 경우 약 4배의 성능을 제공하는 향상된 통합 환경으로 업그레이드를 요청할 수 있습니다. 이 문서에서는 Pro 고객과 Starter 고객을 위한 지침을 구분합니다.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 통합 환경 개선 요청 - Pro 및 Starter

Adobe Commerce on cloud infrastructure Pro 계획 아키텍처 고객이고 현재 표준 크기의 통합 환경을 사용하는 경우 또는 Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 고객이고 현재 표준 크기의 스테이징 환경을 사용하는 경우 약 4배의 성능을 제공하는 향상된 통합 환경으로 업그레이드를 요청할 수 있습니다. 이 문서에서는 Pro 고객과 Starter 고객을 위한 지침을 구분합니다.

>[!NOTE]
>
> 향상된 통합으로 업그레이드하면 타사 통합 또는 사용자 지정을 포함하여 설치의 총 리소스 요구 사항에 따라 달라지므로 모든 성능 문제를 해결하지 못할 수 있습니다.
>
> 또한 통합 환경에서 최고의 성능을 발휘하기 위한 모범 사례를 따르고 있는지 확인해야 하며, 그 조차도 완벽한 솔루션이 아닐 수 있습니다. 지침은 Commerce on Cloud Infrastructure Guide의 [Pro 아키텍처](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) 및 [Starter 아키텍처](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) 설명서를 참조하십시오.

## Pro

1. Pro를 사용하는 경우 업그레이드하려면 통합 분기 수를 두 개로 줄여야 합니다(**주 통합 분기가 총**&#x200B;에 포함됨). **참고: 이 합계에서 기본 분기를 계산하지 마십시오. 기본 분기는 통합 분기로 간주되지 않습니다.** 개발자 설명서에서 [Cloud Console을 사용하여 분기 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=ko)의 단계를 따릅니다.
1. 판매자는 연락처 이유 &quot;*클라우드 구성 변경을 요청*&quot;을(를) 사용하여 향상된 통합 환경에 대한 업그레이드를 요청하는 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)해야 합니다.
1. Adobe 고객 엔지니어링 팀이 통합 환경 수를 확인하고 변경을 시작합니다.
1. 업그레이드가 완료되면 판매자에게 티켓에 알림이 전송됩니다.
1. 판매자는 통합 환경을 다시 배포합니다. 개발자 설명서에서 [분기 병합](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch)의 단계를 따릅니다. *참고*: 다음을 실행하면 배포가 자동으로 수행됩니다. <pre>git 푸시 원본 &lt;branch-name></pre>

향상된 성능은 향상된 통합 환경으로 성공적으로 업그레이드했음을 나타냅니다.

**메모**:

* 표준 크기와 향상된 크기는 사용할 수 있는 두 가지 크기입니다.
* 지정된 저장소의 모든 통합 환경은 크기가 같습니다. 크기를 독립적으로 조정할 수 없습니다.
* 두 개 이상의 향상된 통합 환경이 필요한 경우 Adobe 계정 팀에 문의하십시오.

## 스타터

1. 스타터 플랜에는 통합 분기가 있을 수 없습니다. 판매자는 통합 환경을 삭제하고 스테이징 환경만 남겨야 합니다. 개발자 설명서에서 [Cloud Console을 사용하여 분기 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=ko)의 단계를 따릅니다. 사용 가능한 환경 수가 줄어 최대 하나의 통합 환경을 허용합니다.
1. 판매자는 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 향상된 통합 환경에 대한 업그레이드를 요청해야 합니다. 연락처 이유 *&quot;클라우드 구성 변경을 요청&quot;* - **스테이징 환경이 이름이 지정된 통합 환경입니다**.
1. Adobe 고객 엔지니어링 팀이 통합 환경 수를 확인하고 변경을 시작합니다.
1. 업그레이드가 완료되면 판매자에게 티켓에 알림이 전송됩니다.
1. 판매자는 통합 환경을 다시 배포합니다. 개발자 설명서에서 [분기 병합](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch)의 단계를 따릅니다. *참고*: 다음을 실행하면 배포가 자동으로 수행됩니다. <pre>git 푸시 원본 &lt;branch-name></pre>

향상된 성능은 향상된 통합 환경으로 성공적으로 업그레이드했음을 나타냅니다.

**메모**:

* 표준 크기와 향상된 크기는 사용할 수 있는 두 가지 크기입니다.
* 지정된 저장소의 모든 통합 환경은 크기가 같습니다. 크기를 독립적으로 조정할 수 없습니다.
* 스테이징 이외의 통합 환경이 필요한 경우 Adobe 계정 팀에 문의하십시오.
* 2020년 9월 17일 이후에 구입한 경우 통합 환경 확대로 인해 이 개선 사항을 적용할 수 없습니다.
