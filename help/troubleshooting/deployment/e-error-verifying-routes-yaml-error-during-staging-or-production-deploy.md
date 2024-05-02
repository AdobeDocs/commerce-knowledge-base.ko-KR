---
title: 'E: 스테이징 또는 프로덕션 배포 중 routes.yaml 오류를 확인하는 동안 오류 발생'
description: '"이 문서에서는 스테이징 또는 프로덕션 환경에 프로젝트를 배포할 때 *"E: route.yaml"* 오류 메시지를 받는 클라우드 인프라 문제에 대한 Adobe Commerce 솔루션을 제공합니다."'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: 스테이징 또는 프로덕션 배포 중 routes.yaml 오류를 확인하는 도중 오류 발생

이 문서에서는 다음과 같은 이점을 얻을 수 있는 Adobe Commerce on cloud infrastructure 문제에 대한 솔루션을 제공합니다. *&quot;E: routes.yaml 를 확인하는 중 오류 발생&quot;* 스테이징 또는 프로덕션 환경에 프로젝트를 배포하려는 경우 오류 메시지가 표시됩니다.

## 영향을 받는 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

<u>재현 단계</u>:

스테이징 또는 프로덕션 환경에 코드를 푸시하여 배포를 트리거합니다.

<u>예상 동작</u>:

배포가 완료되었습니다.

<u>실제 동작</u>:

배포가 차단되고 다음 오류 메시지가 로그에 표시됩니다.

<pre>응용 프로그램 배포 구성 E 확인 중: routes.yaml을 확인하는 동안 오류가 발생했습니다.
다음 도메인은 클러스터에 대해 구성되었지만 routes.yaml 파일에 정의된 경로가 없습니다. - store1.example.com - store2.example.com - test-store.example.com 현재 routes.yaml 구성을 사용하면 이러한 도메인이 제공되지 않습니다!

계속하려면 문제 해결 지침을 보려면 여기 를 참조하십시오. /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## 원인

이 오류는 프로젝트에 추가된 모든 추가 도메인에 대한 경로 구성이 다음에서 누락된 경우 발생합니다. `routes.yaml` 파일.

셀프서비스 경로 구성을 위한 Adobe Commerce 셀프서비스 지원 업그레이드의 일부로 프로젝트의 모든 도메인에 `routes.yaml` 파일. 도메인에서 경로 구성이 누락된 경우 배포가 차단됩니다.

## 솔루션

차단된 배포를 해결하려면 `routes.yaml` 다음 방법 중 하나를 사용하여 오류 메시지에 나열된 도메인의 경로를 구성하는 파일입니다.

* 업그레이드 프로세스 중에 Adobe Commerce에서 제공한 패치를 적용합니다.
* 누락된 경로 구성을 수동으로 `routes.yaml` 파일.

### 방법 1: Adobe Commerce에서 제공한 패치 적용

1. 제목이 인 최근 Adobe Commerce 지원 티켓을 찾습니다.*다음에 대한 셀프서비스 기능 활성화 &lt;project _id=&quot;&quot;>&quot;.*
1. 티켓의 지침에 따라 패치를 적용하면 클라우드 환경에 대한 경로 구성이 업데이트됩니다.
1. 변경 с 사항을 생략하고 푸시하여 프로젝트를 재배포합니다.

### 방법 2: 누락된 경로 구성을 수동으로 추가

1. 동일한 경로 구성을 사용하여 프로젝트의 모든 도메인을 제공하려면 다음을 업데이트하십시오. `routes.yaml` 다음 예와 같이 프로젝트의 기본 도메인과 다른 모든 도메인에 대한 경로 템플릿을 추가하는 파일:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. 변경 с 사항을 생략하고 푸시하여 프로젝트를 재배포합니다.

경로 구성을 업데이트하는 방법에 대한 자세한 지침은 [Adobe Commerce용 클라우드 > 경로 구성](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_routes.html) 개발자 설명서에서 확인할 수 있습니다.

>[!NOTE]
>
>프로젝트 구성에서 더 이상 사용되지 않는 도메인을 지정하는 경우 다음 단계를 완료하여 가능한 한 빨리 프로젝트에서 제거하십시오. 1. 프로젝트 환경에서 제거할 도메인 목록과 함께 지원 티켓을 제출합니다. 2. 지원 팀이 도메인을 제거한 후 `routes.yaml` 오래된 도메인에 대한 참조를 제거하는 파일입니다.
