---
title: '배포 오류: SQLSTATE[HY000]'
description: 이 문서에서는 SQLSTATE[HY000] 오류로 인해 배포가 실패하는 문제에 대한 해결 방법을 제공합니다.
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# 배포 오류: SQLSTATE[HY000]

이 문서에서는 SQLSTATE[HY000] 오류로 인해 배포가 실패하는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce, [모든 배포 메서드](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

배포 중 SQLSTATE 오류가 발생합니다.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## 원인

배포 중 Cron이 실행되고 있습니다.

## 솔루션

이 문제를 해결하려면 명령줄을 열고 다음 명령을 실행하여 cron의 실행을 중지합니다.
`./vendor/bin/ece-tools cron:disable`.
