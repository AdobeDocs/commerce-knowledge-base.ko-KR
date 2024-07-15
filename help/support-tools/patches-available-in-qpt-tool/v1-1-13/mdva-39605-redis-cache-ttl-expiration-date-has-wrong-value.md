---
title: 'MDVA-39605: Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있습니다.'
description: MDVA-39605 패치는 Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39605입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있습니다.

MDVA-39605 패치는 Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39605입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있습니다.

<u>재현 단계</u>:

수정 사항을 테스트하려면 캐시를 플러시하고 상점 첫 화면에서 구성 가능한 제품을 여십시오. 그런 다음 터미널(콘솔)을 열고 아래 단계를 수행합니다.

1. `redis-cli` 명령을 실행합니다.
1. `KEYS "*PRICE"`을(를) 실행합니다. 결과에 키가 하나만 있어야 합니다(예: `zc:ti:e54_PRICE`). 키를 복사합니다.
1. `SMEMBERS`을(를) 실행한 다음 이전 단계의 키(예: `SMEMBERS zc:ti:e54_PRICE`)를 실행합니다. 결과에서 아무 키나 복사합니다(예: e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. 이전 단계의 키 이름으로 `KEYS "*<key>"`을(를) 실행하여 전체 키 이름(예: `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`)을 가져옵니다. 결과에 키가 하나만 있어야 합니다(예: `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). 알 수 있듯이 전체 키 이름은 단순히 접두사가 &quot;`zc:k:`&quot;인 키 이름입니다. 이제 전체 키 이름을 복사합니다.
1. `HGETALL`을(를) 실행한 다음 4단계의 전체 키 이름을 실행하여 값을 확인합니다. 값에는 관련 구성 가능한 제품의 관련 제품에 대한 일련화된 데이터가 포함되어야 합니다.
1. `TTL`을(를) 실행한 다음 4단계의 전체 키 이름을 실행하여 키에 만료가 있는지 확인합니다. 결과는 **-1** 및 **-2**&#x200B;과(와) 달라야 하며 약 2592000(30일)이어야 합니다. 코드에 설정된 만료일이 1년이지만 Adobe Commerce에서 사용되는 Redis 라이브러리의 최대 만료일 제한은 2592000초입니다.

<u>예상 결과</u>:

만료 한도는 2592000초입니다.

<u>실제 결과</u>:

만료 제한이 **-1** 또는 **-2**(으)로 설정되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
