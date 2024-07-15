---
title: 배포가 실패하여 Adobe Commerce *배포 후 건너뜀* 오류
description: '이 문서에서는 배포 오류를 조사하는 방법에 대해 설명합니다. *배포가 실패했기 때문에 Post 배포를 건너뜁니다.*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# 배포가 실패했으므로 Adobe Commerce *후 배포를 건너뜁니다* 오류

이 문서에서는 배포 오류를 조사하는 방법에 대해 설명합니다. *배포가 실패했기 때문에 Post-deploy를 건너뜁니다*. 이 오류는 업그레이드 등 다른 환경에 배포하는 동안 발생합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 문제

배포가 실패하고 일반적인 오류 메시지를 반환하므로 오류를 해결하는 방법에 대해 명확하지 않습니다.

## 원인

확인되지 않음 - 이 오류 메시지의 원인은 배포된 코드와 데이터베이스에 따라 다릅니다.

## 배포 오류를 조사하는 방법

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

실제 원인을 확인하기 위한 오류 추적을 가져오려면 서버에 SSH를 실행하고 로그 파일 `var/log/install_upgrade.log`을(를) 확인하십시오.
