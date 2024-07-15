---
title: Google Analytics이 전환 데이터를 추적하고 있지 않습니다.
description: 이 문서에서는 전환 데이터를 추적하지 않는 Google Analytics과 관련된 알려진 Adobe Commerce 2.2.4 문제에 대한 패치를 제공합니다.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Google Analytics이 전환 데이터를 추적하고 있지 않습니다.

이 문서에서는 전환 데이터를 추적하지 않는 Google Analytics과 관련된 알려진 Adobe Commerce 2.2.4 문제에 대한 패치를 제공합니다.

>[!NOTE]
>
>Adobe Commerce 2.2.6에서 문제가 해결되었습니다.

## 문제

Google Analytics 구성 요소 코드의 오류로 인해 Google Analytics이 전환 데이터를 추적하지 못했습니다.

<u>재현 단계</u>:

1. **스토어** > **설정** > **구성** > **판매** > **Google API** > **Google Analytics**&#x200B;에서 Commerce 관리자의 Google Analytics 기능을 활성화하고 구성합니다.
1. **구성 저장**&#x200B;을 클릭합니다.
1. 가게 앞에 가서 주문하세요.
1. **Google Analytics 대시보드** > **전환** > **개요**(으)로 이동합니다.
1. 날짜 범위를 현재 날짜로 설정합니다.

<u>예상 결과</u>:

전환 데이터에 순서가 나타납니다.

<u>실제 결과</u>:

전환 데이터에 순서가 표시되지 않습니다.

## 솔루션

이 패치는 Google Analytics 구성 요소 코드의 오류를 수정합니다. 패치 적용 후 변환 데이터는 Google Analytics에 의해 추적됩니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-11263\_EE\_2.2.4\_v1.composer.patch 다운로드](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 온-프레미스 2.2.4

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce 온-프레미스 2.2.5
* 클라우드 인프라의 Adobe Commerce 2.2.4, 2.2.5

## 패치 적용 방법

지침은 [Adobe Commerce에서 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
