---
title: '''setup:static-content:deploy'' deployed_version.txt 문제 실행'
description: 이 문서에서는 'setup:static-content:deploy' 명령을 수동으로 실행할 때 'deployed_version.txt'에 대한 쓰기 불가능 오류가 수정됩니다.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# `setup:static-content:deploy` deployed_version.txt 문제 실행

이 문서에서는 `setup:static-content:deploy` 명령을 수동으로 실행할 때 `deployed_version.txt`에 대한 쓰기 불가능 오류를 수정합니다.

## 문제

Adobe Commerce 클라우드 인프라 권장 사항에 따라 [구성 관리](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md)를 사용하고 배포 중 웹 사이트 가동 중단을 줄이기 위해 정적 에셋 생성을 빌드 단계로 이동하는 경우 `setup:static-content:deploy` 명령을 수동으로 실행할 때 다음 오류가 발생할 수 있습니다.

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## 원인

다운타임을 줄이기 위해 배포 프로세스를 최적화하고 정적 에셋 파일을 복사하는 대신 심볼릭 링크를 만들었습니다. 정적 자산이 저장되는 위치는 읽기 전용이므로 위에 오류 메시지가 표시됩니다.

모든 에셋이 이미 생성되었으며 수동으로 수행하는 경우 파일 간에 차이가 없으므로 정적 콘텐츠 배포를 수동으로 실행하지 않는 것이 좋습니다(테마 파일도 읽기 전용이며 변경할 수 없음). 따라서 이러한 작업에는 의미가 없습니다.

## 솔루션

정적 콘텐츠 배포를 계속 실행하려면 `pub/static` 디렉터리에서 symlink를 제거하고 `setup:static-content:deploy` 명령을 다시 실행하십시오.

```
find pub/static/ -maxdepth 1 -type l -delete
```
