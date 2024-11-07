---
title: Commerce 관리자의 캐시를 제거하는 동안 오류 발생
description: '이 문서에서는 Commerce 관리자의 캐시를 제거할 때 발생하는 오류 메시지의 원인을 식별하는 방법에 대해 설명합니다. 관리자를 통해 캐시를 제거하려고 하면 다음과 같은 메시지가 표시됩니다.'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Commerce 관리자의 캐시를 제거하는 동안 오류 발생

이 문서에서는 Commerce 관리자의 캐시를 제거할 때 발생하는 오류 메시지의 원인을 식별하는 방법에 대해 설명합니다. 관리자를 통해 캐시를 제거하려고 하면 다음과 같은 메시지가 표시됩니다.
*/app/project-id/pub/media/catalog/product/cache/directory/filename&quot; 파일은 삭제할 수 없습니다. 경고!unlink(/app/project id/pub/media/catalog/product/cache/directory/filename): 해당 파일 또는 디렉터리가 없습니다.*

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 방법) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## 문제

관리자를 통해 캐시를 제거하려고 하면 오류 메시지가 표시됩니다.

<u>재현 단계:</u>

1. 관리에서 **시스템** > **도구** > **캐시 관리**(으)로 이동합니다.
1. 캐시 지우기 옵션 중 하나를 선택합니다.

<u>예상 결과:</u>

오류 없이 Adobe Commerce 캐시를 성공적으로 플러시했습니다.

<u>실제 결과:</u>

&quot;파일을 삭제할 수 없습니다.&quot; 오류가 표시됩니다.

## 원인

이 오류는 캐시 정리 작업이 시작된 시간과 완료된 것으로 보고된 시간 사이의 지연과 관련이 있습니다.

## 솔루션

1. 오류에 언급된 파일이 서버에 없는지 확인합니다(캐시 제거가 성공했는지 확인).

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

다음 출력이 표시되는 경우

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

작업이 이미 완료되었을 때 파일을 지우려고 했습니다. 버그가 아닙니다. 가끔씩 발생할 것으로 예상되는 메시징 동시성 문제입니다. 문제를 해결할 수 있는 문제는 없습니다.
그러나 출력에서 파일이 캐시에 남아 있는 것으로 표시되면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)해야 합니다.

## 관련 읽기

* 개발자 설명서에서 [캐시 관리](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management).
