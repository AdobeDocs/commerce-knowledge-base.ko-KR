---
title: 성능 문제를 일으키는 제한된 관리자 액세스
description: 이 문서에서는 사용자 안내서에서 [웹 사이트에 의해 제한된 역할 범위의 관리자 역할](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources)을 사용함으로써 성능에 부정적인 영향을 미치는 경우에 대한 솔루션을 제공합니다.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# 성능 문제를 일으키는 제한된 관리자 액세스

이 문서에서는 사용자 안내서에서 [웹 사이트에 의해 제한된 역할 범위의 관리자 역할](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources)을(를) 사용하여 성능에 부정적인 영향을 미치는 경우에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x

## 문제

웹 사이트에 의해 역할 범위가 제한된 관리 사용자가 관리 패널에서 작업(로그인, 제품 저장 등)을 수행하면 Adobe Commerce이 저장된 캐시를 다시 빌드합니다. 캐시를 재구축하면 성능에 부정적인 영향을 미치며, 특히 업무 및/또는 높은 트래픽 시간 중에 사이트 중단이 발생할 수 있습니다.

이 문제는 Adobe Commerce 2.2.10 및 2.3.3에서 해결되었습니다.

## 솔루션

다음은 이 문제를 방지하는 옵션입니다.

* Adobe Commerce 애플리케이션 버전을 2.2.10 또는 2.3.3으로 업그레이드하십시오. 자세한 내용은 개발자 설명서에서 [클라우드 인프라의 Adobe Commerce 업그레이드](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)를 참조하십시오.
* 가능한 경우 웹 사이트별로 관리자 사용자 역할 범위를 제한하지 마십시오.
* [Magento 지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 가능한 경우 패치를 요청합니다.

## 관련 읽기

* 사용 안내서의 [사용자 역할](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/user-accounts/permissions-user-roles).
