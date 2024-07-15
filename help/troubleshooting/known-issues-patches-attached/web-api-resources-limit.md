---
title: 웹 API가 배열에 20개 이상의 항목이 있는 요청을 처리할 수 없음
description: 이 문서에서는 웹 API가 Adobe Commerce 2.4.3용 배열에 20개 이상의 항목이 포함된 메시지를 처리할 수 없는 문제에 대한 해결 방법을 제공합니다.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# 웹 API가 배열에 20개 이상의 항목이 있는 요청을 처리할 수 없음

이 문서에서는 웹 API가 Adobe Commerce 2.4.3용 배열에 20개 이상의 항목이 포함된 메시지를 처리할 수 없는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전:

* Adobe Commerce(모든 배포 방법) 2.4.3 및 2.3.7-p1
* Magento Open Source 2.4.3 및 2.3.7-p1

## 문제

웹 API가 배열에 20개 이상의 항목이 포함된 메시지(예: Stock 업데이트)를 처리할 수 없습니다.

## 원인

Adobe Commerce 2.4.3에서는 서비스 거부(DoS) 공격을 방지하기 위해 Magento API에 내장된 속도 제한이 추가되었습니다.

기본적으로 다음과 같은 기본 제공 API 속도 제한을 사용할 수 있습니다.

* 엔티티 목록을 나타내는 입력을 포함하는 REST 요청은 기본적으로 최대 20개의 엔티티로 제한됩니다
* 페이지가 매겨진 결과를 허용하는 REST 및 GraphQL 쿼리는 페이지당 기본 최대 300개의 항목으로 제한됩니다

## 솔루션

REST API 요청에 대한 입력 제한을 비활성화하려면 버전에 따라 다음 패치 중 하나를 적용합니다.

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### 호환 가능한 Adobe Commerce 버전

패치는 다음에 대해 생성되었습니다.

* 클라우드 인프라 2.4.3 및 2.3.7-p1의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.4.3 및 2.3.7-p1

패치는 다른 Adobe Commerce 버전과 호환되지 않습니다.

### 패치 적용 방법

[Adobe에서 제공하는 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)에 설명된 대로 다운로드한 `.zip` 파일의 압축을 풀고 패치를 적용합니다.

>[!WARNING]
>
>스토어에서 DoS 공격이 발생하고 있다고 의심되는 경우 Adobe은 기본 입력 제한을 더 낮은 값으로 낮추어 요청할 수 있는 리소스 수에 제한을 두는 것을 권장합니다.  [클래스 생성자 인수](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)를 사용하여 프로그래밍 방식으로 기본 제한을 사용자 지정할 수 있습니다.
>개발자 설명서에 설명된 대로: [API 보안 > 속도 제한 > 최대 매개 변수 입력](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## 관련 읽기

개발자 설명서에서 [API 보안 > 속도 제한](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).
