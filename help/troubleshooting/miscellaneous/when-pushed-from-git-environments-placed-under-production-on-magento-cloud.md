---
title: Git에서 푸시할 때 프로덕션에 배치되는 새 환경
description: 이 문서에서는 git 버전 제어 시스템에서 푸시할 때 클라우드 인프라의 Adobe Commerce에서 프로덕션 환경 아래에 새 환경이 배치되는 문제에 대한 솔루션을 제공합니다.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Git에서 푸시할 때 프로덕션에 배치되는 새 환경

이 문서에서는 git 버전 제어 시스템에서 푸시할 때 클라우드 인프라의 Adobe Commerce에서 프로덕션 환경 아래에 새 환경이 배치되는 문제에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 문제

<u>필수 구성 요소</u>:

프로젝트의 로컬 git 제어 복제본이 있습니다.

<u>재현 단계</u>:

스테이징 분기에서 통합 분기를 만들어야 합니다.

1. 로컬 셸에서 다음 명령을 실행하여 스테이징 분기로 전환합니다. `git checkout staging`
1. 로컬 셸에서 다음 명령을 실행하여 스테이징 분기에서 통합 분기를 만듭니다. `git checkout -b <branch>`
1. 로컬 셸에서 다음 명령을 실행하여 원격 리포지토리에 분기를 푸시하고 업스트림 분기를 설정합니다. `git push --set-upstream origin <branch>`

<u>예상 결과</u>:

새 분기는 스테이징 분기 아래에 생성됩니다.

<u>실제 결과</u>:

생산 지점 아래에 새 지점이 생성되었습니다.

## 원인

버그가 아닙니다. 다른 분기의 상위 분기를 설정하려면 판매자가 magento-cloud CLI를 사용해야 합니다.

## 솔루션

상위 지점은 가맹점이 새로 만든 지점을 밀고 활성화한 후에만 설정할 수 있다. 개발자 설명서에서 [클라우드 인프라의 Adobe Commerce > Bitbucket 통합](https://devdocs.magento.com/cloud/integrations/bitbucket-integration.html#create-a-new-cloud-branch)을 참조하십시오.

서버의 기존 분기에 대한 상위 항목을 업데이트하려면 magento-cloud CLI에서 `magento-cloud environment:info` 명령을 사용하십시오.

사용의 예:

`magento-cloud environment:info parent Staging`

이렇게 하면 현재 체크 아웃된 분기에 대해 상위 분기가 &quot;스테이징 중&quot;으로 설정됩니다.

## 관련 읽기

* 개발자 설명서에서 [클라우드 인프라의 Adobe Commerce > magento-cloud CLI](https://devdocs.magento.com/cloud/reference/cli-ref-topic.html).
