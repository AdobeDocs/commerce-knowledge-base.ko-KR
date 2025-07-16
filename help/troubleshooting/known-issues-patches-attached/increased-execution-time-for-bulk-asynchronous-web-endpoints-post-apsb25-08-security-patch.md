---
title: APSB25-08 보안 패치 이후 대량 비동기 웹 엔드포인트의 실행 시간 증가
description: 이 문서에서는 APSB25-08 보안 패치를 적용한 후 1000+ 항목에 대한 POST rest/all/async/bulk/V1/products 요청에서 실행 시간이 크게 증가하는 문제에 대한 핫픽스를 제공합니다.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
exl-id: 784a48cb-1ef1-432b-b09f-ebcbb9bebf01
source-git-commit: f0c2e20e0bd6dab713be59c1c686ee2948445bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# APSB25-08 보안 패치 이후 모든 벌크 비동기 웹 엔드포인트의 실행 시간 증가

이 문서에서는 APSB25-08 보안 패치를 적용한 후 실행 시간이 상당히 긴 1000개 이상의 항목이 있는 `POST rest/all/async/bulk/V1/products`과(와) 같은 모든 대량 비동기 웹 끝점에 대한 핫픽스를 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce(모든 배포 방법) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11

* Adobe Commerce(모든 배포 방법) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce(모든 배포 방법) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce(모든 배포 방법) 2.4.8

## 문제

APSB25-08 보안 패치를 적용한 후 항목이 1000개 이상인 `POST rest/all/async/bulk/V1/products`개의 요청을 실행하는 데 훨씬 더 오래 걸립니다.

<u>재현 단계</u>:

1. 1000개 이상의 항목으로 `POST rest/all/async/bulk/V1/products`을(를) 요청합니다(이름, SKU 및 설명이면 충분함).
1. 요청에 걸린 시간을 확인합니다.
1. APSB25-08 보안 패치를 적용하고 `se:di:co`을(를) 사용하여 생성된 데이터와 캐시를 정리합니다.
1. `bin/magento c:f` 실행.
1. Storefront로 이동하여 캐시와 생성된 파일이 제자리에 있는지 확인합니다.
1. 1단계의 요청을 반복합니다.
1. 요청에 걸린 시간이 늘어났는지 확인합니다.
1. APSB25-08 보안 패치를 제거하고 캐시를 플러시한 다음 코드를 다시 생성하고 1단계의 요청을 반복하여 실행 시간이 정상적으로 반환되는지 확인합니다. (선택 사항)

<u>예상 결과</u>:

보안 패치를 적용한 후 `async/bulk` 요청의 실행 시간이 크게 늘어났습니다.

<u>실제 결과</u>:

시간이 다소 늘어날 수 있지만 보안 패치를 적용한 후에는 `async/bulk` 요청의 실행 시간이 크게 늘어나지 않아야 합니다.

## 솔루션

이 문제를 해결하려면 [AC-14078-2-4x-composer-patch.zip](assets/AC-14078-2-4x-composer-patch.zip)을 적용하세요.

## 패치 적용 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=ko)을 참조하십시오.

## 관련 읽기

* [Adobe Commerce에 보안 업데이트 사용 가능 - APSB25-08](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-27149)
