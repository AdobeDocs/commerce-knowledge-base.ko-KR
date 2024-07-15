---
title: 'MDVA-32759 패치: 공유 카탈로그가 계층 가격 책정 삭제'
description: MDVA-32759 패치는 공유 카탈로그가 기존 계층 가격을 삭제하는 문제를 해결합니다.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-32759 패치: 공유 카탈로그가 계층 가격을 삭제합니다.

MDVA-32759 패치는 공유 카탈로그가 기존 계층 가격을 삭제하는 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.4-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소</u>:

**B2B 기능**&#x200B;이 활성화된 B2B로 Adobe Commerce을 설치합니다.

<u>재현 단계</u>:

1. **스토어 > 구성 > B2B 기능 > 회사 사용** 및 **공유 카탈로그**(으)로 이동합니다.
1. `bin/magento cron:run` 실행.
1. 간단한 제품을 만들고 **고급 가격 설정**&#x200B;을 클릭한 다음 **카탈로그 및 계층 가격**&#x200B;을 추가한 후 저장합니다.
1. **카탈로그 > 공유 카탈로그 > 가격 및 구조 설정**(으)로 이동하고 **구성**&#x200B;을 클릭한 다음 드롭다운 메뉴에서 모든 옵션을 선택 취소하고 저장합니다.
1. `bin/magento cron:run` 실행.
1. 위에서 만든 제품을 열고 고급 가격을 선택합니다.

<u>예상 결과</u>:

예상대로 공개 공유 카탈로그에서 모든 제품을 제거한 후 제품에서 계층 가격을 제거해서는 안 됩니다.

<u>실제 결과</u>:

공개 공유 카탈로그에서 모든 제품을 제거한 후 계층 가격을 제거합니다.


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
