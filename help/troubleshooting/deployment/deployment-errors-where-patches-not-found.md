---
title: 배포 또는 수동 응용 프로그램 중 패치에 오류가 없습니다.
description: '이 문서에서는 오류가 발생하는 문제에 대한 해결 방법을 제공합니다. *다음 패치를 찾을 수 없는 경우: MDVA-XXXXX, ACSD-XXXXX. ''status'' 명령*을 사용하여 현재 Magento 버전에 대한 이러한 패치의 가용성을 확인하십시오.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: be0c72a1759ba172666c7c9409c65a1a388e3f11
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 배포 또는 수동 응용 프로그램 중 패치에 오류가 없습니다.

이 문서에서는 인스턴스 업그레이드가 실패하고 배포 로그에 오류가 표시되는 문제에 대한 해결 방법을 제공합니다. *다음 패치를 찾을 수 없음: MDVA-XXXXX, ACSD-XXXXX. &quot;status&quot; 명령*&#x200B;을(를) 사용하여 현재 Magento 버전에 대한 이러한 패치의 가용성을 확인하십시오.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 문제

Adobe Commerce을 업그레이드할 때 오류가 발생했습니다. *다음 패치를 찾을 수 없습니다*.

## 원인

이전 버전에 대해 이전에 적용된 패치는 새 버전에 적용할 수 없거나 더 이상 사용할 수 없습니다.

이 문제는 설치된 품질 패치 도구 패키지(`magento/quality-patches`)가 오래된 경우에도 발생할 수 있습니다.

For example:

사례 1:
* 원래 QPT 1.1.71에서 2.4.7-p9에 대해 패치를 사용할 수 있었습니다
* 최신 QPT 릴리스(예: 1.1.72)는 나중에 2.4.7-p10을 지원할 수 있습니다
* 고객이 Commerce을 2.4.7-p10으로 업그레이드하지만 이전 QPT 버전이 설치된 경우 QPT는 2.4.7-p10에 호환되는 패치 변형이 있음을 인식하지 못할 수 있습니다

사례 2:
* QPT 1.1.72에 패치가 추가되었을 수 있습니다
* 고객이 이전 QPT 버전을 설치한 경우 QPT는 패치가 있음을 인식하지 못합니다

이러한 경우 패치를 적용하면 다음과 같은 메시지가 나타나면서 실패할 수 있습니다.

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

이 문제는 설치된 QPT 버전이 현재 Commerce 버전을 해당 패치 버전에 매핑할 수 없기 때문에 발생합니다.

## 솔루션

이 문제는 `.magento.env.yaml`을(를) 통해 패치를 적용하는 배포에만 국한되지 않습니다. 다음을 사용하여 패치를 수동으로 적용할 때도 동일한 문제가 발생할 수 있습니다.

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

For example:

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

이 경우 명령이 실행되는 환경에 설치된 Adobe Commerce 버전에는 패치를 사용할 수 없습니다.

1. QUALITY_PATCHES 섹션에서 `.magento.env.yaml` 파일을 확인합니다. 예:

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. [품질 패치 릴리스 정보](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=ko)에서 패치 ID를 검색하여 업그레이드하려는 새 버전의 Adobe Commerce에 각 ID를 적용할 수 있는지 확인하십시오.
1. 패치를 업그레이드하려는 새 버전의 Adobe Commerce에 적용할 수 없는 경우 `.magento.env.yaml` 파일에서 패치 ID를 제거하십시오.
1. 오류로 표시된 모든 패치 ID를 검토한 후 변경 사항을 푸시하고 다시 배포합니다.

## 관련 읽기

* Commerce on Cloud Infrastructure Guide의 [패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko#apply-a-patch-in-a-local-environment).

