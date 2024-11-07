---
title: 분할 데이터베이스 솔루션의 고급 보고 404 오류
description: 이 문서에서는 고급 보고를 사용하려고 할 때 404 오류가 발생하는 [split database solution](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)을 사용하는 Adobe Commerce 2.3.x 사용자를 위한 패치를 제공합니다.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 분할 데이터베이스 솔루션의 고급 보고 404 오류

이 문서에서는 고급 보고를 사용하려고 할 때 404 오류가 발생하는 [분할 데이터베이스 솔루션](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)을 사용하는 Adobe Commerce 2.3.x 사용자를 위한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce 2.3.0 - 2.3.5-p1

## 문제

이 패치를 사용하면 따옴표 데이터를 수집하는 데 잘못된 연결 이름이 사용되는 문제가 해결됩니다. 잘못된 연결 이름이 사용되기 때문에 견적 데이터가 Magento Business Intelligence(MBI)로 전송되지 않고 보고서를 생성할 수 없습니다.

## 솔루션

이 문서에 제공된 [패치](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)를 적용합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 다음 링크를 클릭하십시오.

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## 패치 적용 방법

파일의 압축을 풀고 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)의 지침을 따릅니다.
