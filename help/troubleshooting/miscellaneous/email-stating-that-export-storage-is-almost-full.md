---
title: 내보내기 저장소가 거의 꽉 찼음을 알리는 이메일
description: 이 문서에서는 내보내기 저장소가 거의 가득 찼다는 내용의 이메일을 받는 문제에 대한 해결 방법을 제공합니다.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 내보내기 저장소가 거의 꽉 찼다는 이메일

이 문서에서는 내보내기 저장소가 거의 가득 찼다는 내용의 이메일을 받는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

다음 내용이 포함된 전자 메일을 받았지만 *내보내기* 폴더를 찾을 수 없습니다.

*모니터링에서 클러스터 XXX의 &#39;내보내기&#39; 저장소가 &#39;85%&#39; 정도 찼음을 발견했습니다.*
*필요한 경우 사용을 검토하거나 정리를 수행하거나 업사이징을 요청하십시오.*
*또한 저장소가 중요 임계값 수준에 도달하면 자동으로 업사이징을 시도합니다.*

## 원인

이메일은 파일/미디어에 할당된 디스크 양인 **exports** 저장소를 참조하며 *exports*(이)라는 특정 폴더는 아닙니다.

## 솔루션

환경에서 파일 사용을 검토해야 합니다. 이 명령을 실행하여 기존 사용량을 가져옵니다.

`df -h |grep data`

파일 저장소가 가득 찬 일반적인 위치는 *pub/media/catalog/product/cache* 또는 *var/log* 폴더입니다. 파일에서 사용하는 디스크 공간을 확인하려면 적절한 경로 */path/to/folder*(으)로 이 명령을 실행하십시오.

`du -shc` */path/to/folder*

미디어 디스크 사용량이 전체 디스크 공간의 큰 부분을 차지하는 경우 [Fastly Deep Image Optimization](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)을(를) 활성화한 다음 서버의 *pub/media/catalog/product/cache* 폴더에서 파일을 수동으로 삭제할 수 있습니다.

## 관련 읽기

지원 기술 자료에서 [전용 클러스터를 확인](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters)하세요.
