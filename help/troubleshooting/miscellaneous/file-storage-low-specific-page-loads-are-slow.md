---
title: 파일 스토리지 부족, 특정 페이지 로드 속도가 느림
description: 이 문서에서는 크고 풍부한 이미지로 인해 디스크 공간이 부족해지는 문제에 대한 해결 방법을 제공합니다.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 파일 스토리지 부족, 특정 페이지 로드 속도가 느림

이 문서에서는 크고 풍부한 이미지로 인해 디스크 공간이 부족해지는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 지원되는 모든 버전
* Adobe Commerce 온-프레미스, 지원되는 모든 버전
* Magento Open Source, 지원되는 모든 버전

## 문제

전용 스테이징 환경이 프로비저닝되지 않은 경우 `pub/media/catalog/products`에서 많은 양의 저장소를 사용하고 스테이징과 프로덕션 사이의 디스크 공간 공유를 사용하는 크고 풍부한 이미지로 인해 디스크 저장 공간이 부족하고 페이지 로드가 느려질 수 있습니다.

## 원인

이미지가 성능과 보기 품질의 균형을 이루도록 최적화되지 않았습니다.

## 솔루션

이미지를 업로드하기 전에 최적화하고 압축하여 성능과 보기 품질의 균형을 유지합니다. 이렇게 하면 공간이 늘어나고 페이지 로드 시간이 줄어듭니다. PNG는 단색의 넓은 영역이 있는 이미지에 대해 더 작은 크기를 제공합니다. JPEG은 다른 모든 것에 비해 작은 크기를 제공합니다. 가장 높은 압축을 사용합니다(눈에 띄는 성능 저하 없이). 이는 일반적으로 60~80%입니다.

보다 효율적인 저장 공간 이미지를 만들려면 [빠른 이미지 최적화](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html)를 사용하십시오.

## 관련 읽기

디스크 공간 관리에 대한 자세한 내용은(클라우드 인프라의 Adobe Commerce에 있는 경우) Commerce on Cloud Infrastructure Guide의 [Adobe Commerce에서 디스크 공간 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html)를 참조하십시오.
