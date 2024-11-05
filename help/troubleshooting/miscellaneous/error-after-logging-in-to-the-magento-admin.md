---
title: Commerce 관리자에 로그인한 후 오류 발생
description: 이 문서에서는 요청된 URL을 이 서버에서 찾을 수 없다는 오류 메시지가 표시되는 문제에 대한 해결 방법을 제공합니다.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Commerce 관리자에 로그인한 후 오류 발생

이 문서에서는 요청된 URL을 이 서버에서 찾을 수 없다는 오류 메시지가 표시되는 문제에 대한 해결 방법을 제공합니다.

## 세부 사항

요청한 URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/을(를) 이 서버에서 찾을 수 없습니다.

URL에서 `magento2`과(와) `index.php` 사이에 슬래시 문자가 없습니다.

## 솔루션

기본 URL이 올바르지 않습니다. 기본 URL은

* `http://` 또는 `https://`(으)로 시작
* 슬래시( `/`)로 끝남
* `core_config_data` 데이터베이스 테이블에서 `web/unsecure/base_url` 레코드의 대/소문자를 일치시키십시오

올바른 값을 사용하여 설치를 다시 실행합니다.

## 관련 읽기

Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
