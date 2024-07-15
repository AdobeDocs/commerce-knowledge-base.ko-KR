---
title: Nginx(경로) 대신 Fastly로 리디렉션되지 않는 리디렉션 오프로드
description: 이 항목에서는 클라우드 인프라에서 Adobe Commerce의 Nginx 대신 Fastly로 리디렉션을 오프로드할 때 발생할 수 있는 일반적인 리디렉션 성능 문제에 대한 해결 방법을 제안합니다.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Nginx(경로) 대신 Fastly로 리디렉션되지 않는 리디렉션 오프로드

이 항목에서는 클라우드 인프라에서 Adobe Commerce의 Nginx 대신 Fastly로 리디렉션을 오프로드할 때 발생할 수 있는 일반적인 리디렉션 성능 문제에 대한 해결 방법을 제안합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라(모든 버전) `Master/Production/Staging` 환경에서 Fastly를 활용하는 Adobe Commerce

## 문제

클라우드 인프라의 Adobe Commerce에서는 Nginx 계층에서 많은 수의 비-regex 리디렉션/재작성을 수행할 수 없으므로, 성능 문제가 발생할 수 있습니다.

## 원인

`.magento/routes.yaml` 디렉터리의 `routes.yaml` 파일은 클라우드 인프라의 Adobe Commerce 경로를 정의합니다.

`routes.yaml` 파일의 크기가 32KB 이상인 경우 Fastly로 regex가 아닌 리디렉션/다시 쓰기를 오프로드해야 합니다.

이 Nginx 레이어는 많은 양의 비-regex 리디렉션/재쓰기를 처리할 수 없습니다. 그렇지 않으면 성능 문제가 발생합니다.

## 솔루션

해결 방법은 Fastly로 리디렉션하는 리디렉션을 대신 오프로드하는 것입니다. Fastly로 리디렉션할 일반 오류 경로를 만듭니다.

다음 단계에서는 Nginx 대신 Fastly에 리디렉션을 배치하는 방법을 자세히 설명합니다.

1. Edge 사전 만들기

   먼저 [Adobe Commerce의 VCL 코드 조각](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)을 사용하여 Edge 사전을 정의할 수 있습니다. 여기에는 리디렉션이 포함됩니다.

   이에 대한 몇 가지 주의 사항:

   * Fastly는 사전 항목에 대한 regex를 수행할 수 없습니다. 정확히 일치할 뿐입니다. 이러한 제한 사항에 대한 자세한 내용은 [Edge 사전 제한에 대한 Fastly의 문서](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations)를 참조하십시오.
   * Fastly는 단일 사전에서 1000개의 항목으로 제한됩니다. Fastly는 이 한계를 확장할 수 있지만, 세 번째 주의로 이어진다.
   * 항목을 업데이트하고 업데이트된 VCL을 모든 노드에 배포할 때마다 사전을 확장하여 기하학적인 로드 시간이 늘어납니다. 즉, 2000개 시작 사전이 실제로 1000개 시작 사전보다 3x-4x 느리게 로드됩니다. 그러나 이는 VCL을 배포(사전을 업데이트하거나 VCL 함수 코드를 변경)할 때만 문제가 됩니다.

     Fastly가 요청을 처리하는 데 걸리는 시간에는 영향을 주지 않습니다. Fastly가 새로운 구성을 푸시하는 데 걸리는 시간에는 영향을 줍니다.

     일반적으로 구성 변경은 평균적으로 몇 초 정도 걸리며 일반적으로 5~10초 이내로 이루어집니다. 따라서 사전 항목이 2배 증가하면 구성이 롤아웃되는 데 30초 이상 걸립니다. 4배 증가하면 2분에 가까워집니다. 이것은 네 번째 주의로 이어진다.

   * 가장자리 사전에는 10,000개의 항목이라는 상당히 엄격한 제한이 있다.

   리디렉션 목록을 통합하는 것이 좋습니다. 여러 사전을 사용할 수 있지만 VCL에 대한 모든 업데이트는 실제로 Fastly에서 채우는 데 몇 분이 소요됩니다.

1. URL을 사전에 비교합니다.

   URL 조회가 발생할 때, 일치하는 항목이 있는 경우 사용자 지정 오류 코드를 적용하기 위한 비교가 수행됩니다.

   다른 VCL 코드 조각을 사용하여 `vcl_recv`에 다음과 같은 항목을 추가하십시오.

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   여기서는 테이블 항목에 URL이 있는지 확인하는 중입니다. 그럴 경우, 내부 Fastly 오류를 호출하고 해당 오류에 테이블의 리디렉션 URL을 전달합니다.

1. 리디렉션을 관리합니다.

   일치 항목이 발견되면 해당 `obj.status`에 대해 정의된 작업이 수행됩니다(이 경우 301 영구 이동 리디렉션).

   `vcl_error`에서 최종 코드 조각을 사용하여 301 오류 코드를 클라이언트로 다시 보냅니다.

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   이 블록을 사용하여 `vcl_recv`에서 전달된 오류 코드와 일치하는지 확인하고 있으며 일치하는 경우 전달된 오류 메시지로 위치를 설정한 다음 상태 코드를 301로 변경하고 메시지를 &quot;영구적으로 이동됨&quot;으로 변경합니다. 이 시점에서 응답은 클라이언트로 돌아갈 준비가 되어 있어야 합니다.

### 스테이지 서비스

>[!WARNING]
>
>이 모든 단계를 수행하려는 경우 Adobe Commerce 스테이징 환경을 설정하는 것이 좋습니다. 그러면 Fastly 서비스에 대해 테스트를 실행하여 모든 것이 예상대로 작동하는지 확인할 수 있습니다.

Adobe Commerce 스테이징 환경을 실행하지 않으려 하지만 이러한 리디렉션의 모습을 확인하고 싶은 경우 Fastly에서 직접 스테이지 계정을 설정할 수 있습니다.

## 관련 읽기

* [Fastly VCL 참조](https://docs.fastly.com/vcl/)
* 개발자 설명서에서 [경로 구성](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html).
* 개발자 설명서에서 [Fastly를 설정](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html).
* 개발자 설명서에서 [VCL 정규식 치트 시트](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet).
