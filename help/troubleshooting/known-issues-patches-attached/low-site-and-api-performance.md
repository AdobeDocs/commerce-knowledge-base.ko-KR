---
title: 낮은 사이트 및 API 성능
description: 이 문서에서는 'debug.log'를 작성하는 데 필요한 시간이 길어 사이트 및 API 성능이 저하되는 것과 관련된 클라우드 인프라 2.2.1의 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 낮은 사이트 및 API 성능

이 문서에서는 `debug.log`을(를) 작성하는 데 필요한 시간이 길어 사이트 및 API 성능이 낮은 것과 관련된 클라우드 인프라 2.2.1의 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.

## 문제

사이트 성능이 느립니다. `PUT` 메서드를 사용하여 제품을 업데이트하는 등 API 작업이 느리게 실행됩니다. New Relic을 사용한 작업을 자세히 살펴보면 `/var/log/debug.log`에 쓰는 데 대부분의 메모리와 CPU가 사용됩니다.

## 솔루션

문제를 해결하려면 패치를 적용합니다. 패치는 로그, 결제 및 배송 방법 로그를 분리해 별도의 파일에 기록합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch 다운로드](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### 호환 가능한 Adobe Commerce 버전

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.2.1

이 패치는 다음 Adobe 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라 2.2.0, 2.2.2, 2.2.3의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.2.0, 2.2.2, 2.2.3

## 패치 적용 방법

자세한 내용은 지원 기술 자료에서 [Adobe Commerce에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
