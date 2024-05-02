---
title: 클라우드 인프라의 Adobe Commerce에서 디스크 공간이 부족할 때 파일을 안전하게 삭제
description: 이 문서에서는 디스크 공간이 부족하여 파일을 안전하게 제거해야 하는 경우에 대한 해결 방법을 제공합니다. 이 작업을 고려하기 전에 개발자 설명서에서 [디스크 공간 관리](https://devdocs.magento.com/cloud/project/manage-disk-space.html#no-space-left)를 검토하십시오. 해당 문서의 단계가 적합하지 않거나 문제를 해결할 수 없는 경우 이 문서의 단계를 검토하십시오.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 6af353bb379ee88248342a7cb514dd9d36d47a92
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에서 디스크 공간이 부족할 때 파일을 안전하게 삭제

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce: 2.3.0-2.3.7, 2.4.0-2.4.2-p1
* 이는 전용 Pro 클러스터에만 해당됩니다. 시작 및 통합 환경은 단일 노드이며 `/data/exports` 디렉토리.

## 디스크 공간이 부족하다는 징후

디스크 공간이 부족하면 배포 중단, 디스크 가득 참 경고 및 성능 저하가 발생할 수 있습니다.
파일 시스템에서 사용하는 디스크 공간을 보려면 CLI/Terminal에서 다음 명령을 실행합니다.

`df -h`


## 디스크 공간을 늘리기 위해 파일을 안전하게 삭제하는 방법

애플리케이션의 마운트 지점, `/app` 경로 또는 통과 `/mnt/shared`. 동일한 파일에 액세스하는 두 가지 방법입니다.

>[!WARNING]
>
>**의 콘텐츠를 수정하거나 삭제하지 않음`/data/exports`**.
>
>`/data/exports` 는 공유 파일 시스템 뒤의 기본 스토리지이며 GlusterFS에서 관리합니다.
>
>파일 시스템에는 파일 내용뿐만 아니라 클러스터의 노드 간에 동기화를 허용하는 파일 시스템 상태에 대한 메타데이터도 포함되어 있습니다. **이 파일 시스템 내에서 직접 파일을 변경하거나 삭제하면 공유 >파일 시스템이 손상되어 광범위한 복구 또는 데이터 복구가 필요합니다.**

지우는 데 좋은 후보일 수 있는 가장 큰 파일을 찾으려면 다음 명령을 실행합니다(규모가 크거나 사용 중인 프로젝트에서는 최대 1시간이 소요될 수 있음).

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

명령 출력에는 크기가 지정된 가장 큰 파일과 디렉터리 목록이 포함됩니다.

## 관련 읽기

지원 기술 자료에서:

* [클라우드에서 통합 환경을 위한 디스크 공간 증가](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [디스크 공간 부족](/help/troubleshooting/miscellaneous/low-disk-space.md)

개발자 설명서에서:

* [디스크 공간 관리](https://devdocs.magento.com/cloud/project/manage-disk-space.html)
