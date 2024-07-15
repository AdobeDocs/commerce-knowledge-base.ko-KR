---
title: 패치를 찾을 수 없는 배포 오류
description: "이 문서에서는 오류가 발생하는 문제에 대한 해결 방법을 제공합니다. *다음 패치를 찾을 수 없는 경우: MDVA-XXXXX, ACSD-XXXXX. 'status' 명령으로 이러한 패치의 사용 가능 여부를 확인하여 현재 Magento 버전*을 확인하십시오."
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 패치를 찾을 수 없는 배포 오류

이 문서에서는 인스턴스 업그레이드가 실패하고 배포 로그에 오류가 표시되는 문제에 대한 해결 방법을 제공합니다. *다음 패치를 찾을 수 없음: MDVA-XXXXX, ACSD-XXXXX. 현재 Magento 버전*&#x200B;에 대한 이러한 패치의 &quot;status&quot; 명령을 사용할 수 있는지 확인하십시오.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## 문제

Adobe Commerce을 업그레이드할 때 오류가 발생했습니다. *다음 패치를 찾을 수 없습니다*.

## 원인

이전 버전에 대해 이전에 적용된 패치는 새 버전에 적용할 수 없거나 더 이상 사용할 수 없습니다.

## 솔루션

1. PATCH QUALITY_PROPERTIES 섹션에서 `.magento.env.yaml` 파일을 확인합니다. 예:

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. [품질 패치 릴리스 정보](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)에서 패치 ID를 검색하여 업그레이드하려는 새 버전의 Adobe Commerce에 각 ID를 적용할 수 있는지 확인하십시오.
1. 패치를 업그레이드하려는 새 버전의 Adobe Commerce에 적용할 수 없는 경우 `.magento.env.yaml` 파일에서 패치 ID를 제거하십시오.
1. 오류로 표시된 모든 패치 ID를 검토한 후 변경 사항을 푸시하고 다시 배포합니다.

## 관련 읽기

* Commerce on Cloud Infrastructure Guide의 [패치 적용](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment).
