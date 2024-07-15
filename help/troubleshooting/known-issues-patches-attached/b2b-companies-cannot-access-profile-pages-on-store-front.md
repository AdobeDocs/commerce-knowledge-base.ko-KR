---
title: 'B2B: 회사가 매장 전면의 프로필 페이지에 액세스할 수 없음'
description: 이 문서에서는 등록된 회사가 상점 첫 화면의 계정 페이지에 오류를 발생하는 것과 관련된 알려진 Adobe Commerce 2.2.4 B2B 문제에 대한 패치를 제공합니다.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B: 회사가 상점 전면의 프로필 페이지에 액세스할 수 없음

이 문서에서는 등록된 회사가 상점 첫 화면의 계정 페이지에 오류를 발생하는 것과 관련된 알려진 Adobe Commerce 2.2.4 B2B 문제에 대한 패치를 제공합니다.

## 문제

고객(회사)은 사이트에서 회사 계정을 만들 수 있지만 *을(를) 가져옵니다.&quot;customerId = &quot;* 및 *&quot;아직 회사 계정이 없습니다.&quot;* 오류 메시지가 있습니다. 회사 프로필 페이지에 액세스하려고 할 때 *&quot;500 내부 서버 오류&quot;*&#x200B;가 발생할 수도 있습니다.

## 패치

패치를 사용하여 아카이브를 다운로드하려면 다음 링크를 클릭하십시오.

[MDVA-9013\_EE\_2.2.2\_composer.patch 다운로드](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 온-프레미스 2.2.2

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 2.2.0에서 2.2.4로 클라우드 인프라의 Adobe Commerce
* Adobe Commerce 온프레미스 2.2.0에서 2.2.1로, 2.2.3에서 2.2.4로

## 패치 적용 방법

지침은 [Adobe에서 제공한 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.
