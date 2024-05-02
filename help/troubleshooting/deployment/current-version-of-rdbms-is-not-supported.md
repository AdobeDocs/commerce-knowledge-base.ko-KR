---
title: 배포 시 '현재 버전의 RDBMS가 지원되지 않음' 오류 발생
description: '이 문서에서는 배포가 실패하고 배포 로그에 다음 오류가 있는 경우에 대한 솔루션을 제공합니다. *현재 버전의 RDBMS는 지원되지 않음*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# 배포 시 &#39;현재 버전의 RDBMS가 지원되지 않음&#39; 오류 발생

이 문서에서는 배포에 실패하고 배포 로그에 다음 오류가 있는 경우에 대한 솔루션을 제공합니다. *현재 버전의 RDBMS는 지원되지 않습니다.*.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## 문제

이 오류 메시지는 업그레이드하려는 Adobe Commerce 버전에서 현재 MariaDB 버전이 더 이상 지원되지 않으며 MariaDB를 호환 가능한 버전으로 업그레이드해야 함을 의미합니다.


<u>재현 단계</u>:

배포를 시도합니다.

<u>예상 결과</u>:

배포에 성공했습니다.

<u>실제 결과</u>:

배포가 실패하고 다음 오류 메시지가 표시됩니다. *현재 버전의 RDBMS는 지원되지 않습니다.*.

## 원인

사용 중인 MariaDB 버전이 업그레이드하려는 Adobe Commerce 버전과 호환되지 않습니다.

## 솔루션

응용 프로그램을 업그레이드하기 전에 MariaDB 서비스를 호환 가능한 버전으로 업그레이드해야 합니다.


Adobe Commerce on cloud infrastructure Pro 계획 아키텍처(및 스타터 아키텍처의 모든 분기)의 통합 분기에 대해서는 다음을 따르십시오 [서비스 구성](https://devdocs.magento.com/cloud/project/services.html) 개발자 설명서에서 확인할 수 있습니다.

Adobe Commerce on cloud infrastructure Pro 계획 아키텍처의 스테이징 및 프로덕션은 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Adobe Commerce 버전 업그레이드를 배포하기 전에 서비스를 업그레이드하도록 요청하십시오.


## 관련 읽기

* [빌드 및 배포에 대한 우수 사례](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 개발자 설명서에서 확인할 수 있습니다.
* [Adobe Commerce 2.3.5 업그레이드: 컴팩트한 테이블에서 동적 테이블로](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) 를 참조하십시오.
