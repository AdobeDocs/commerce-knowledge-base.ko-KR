---
title: 유지 관리 모드가 활성화되었기 때문에 사이트 로드 실패
description: "이 문서에서는 유지 관리 모드가 계속 활성화되어 있거나 자동으로 비활성화되지 않아 사이트가 로드되지 않는 경우에 대한 수정 사항을 제공합니다. 오류 메시지가 표시될 수 있습니다. *서비스를 일시적으로 사용할 수 없음 유지 관리 다운타임 또는 용량 문제로 인해 서버가 요청을 일시적으로 처리할 수 없습니다.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 유지 관리 모드가 활성화되었기 때문에 사이트 로드 실패

이 문서에서는 유지 관리 모드가 계속 활성화되어 있거나 자동으로 비활성화되지 않아 사이트가 로드되지 않는 경우에 대한 수정 사항을 제공합니다. 오류 메시지가 나타날 수 있습니다. *서비스를 일시적으로 사용할 수 없습니다. 유지 관리 중단 시간 또는 용량 문제로 인해 서버가 요청을 일시적으로 처리할 수 없습니다.*

## 영향을 받는 버전 및 제품

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce 온-프레미스 2.2.x, 2.3.x

## 문제

유지 관리 모드는 배포 프로세스의 일부입니다. 그러나 자동으로 사용으로 설정되었으며 사용 안함으로 설정되지 않았거나, 머천트가 수동으로 유지 관리 모드를 사용으로 설정했으며 사용 안함으로 설정하는 것을 잊어버린 경우 배포가 실패할 수 있습니다.

## 원인

유지 관리 모드를 활성화하면 사이트가 로드되지 않습니다.

## 솔루션

현재 유지 관리 모드 상태를 확인하려면 CLI에서 다음 명령을 실행합니다.

```
bin/magento maintenance:status
```

유지 관리 모드를 해제하려면 CLI에서 다음 명령을 실행합니다.

```
bin/magento maintenance:disable
```

## 관련 읽기

유지 관리 모드를 사용하는 방법에 대해 알아보려면 개발자 설명서에서 [유지 관리 모드 사용 또는 사용 안 함](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)을 참조하세요.
