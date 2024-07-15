---
title: 'MDVA-33106 패치: cron 실행 후 다시 예약된 제품 변경 사항이 지워짐'
description: MDVA-33106 패치는 cron 후에 일정이 잡힌 제품 변경 사항이 지워지는 문제를 해결합니다
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-33106 패치: cron 실행 후 다시 예약된 제품 변경 사항이 지워짐

MDVA-33106 패치는 cron 후에 일정이 잡힌 제품 변경 사항이 지워지는 문제를 해결합니다

```bash
bin/magento cron:run
```

명령이 실행됩니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. Commerce 관리에서 **카탈로그** > **제품**(으)로 이동한 다음 편집을 클릭합니다. **가격** 값을 확인합니다(예: *9.99*).
1. **새 업데이트 예약**&#x200B;을 클릭하고 세부 정보를 입력하십시오.
   * 업데이트 이름은 중요하지 않습니다.
   * 시작 날짜 및 종료 날짜를 +1년으로 미래 날짜로 설정합니다.
   * 가격을 *1.99*(으)로 설정합니다.
   * 변경 사항을 저장합니다.
1. 콘텐츠 스테이징 대시보드로 이동하여 그리드 보기를 선택하여 위에서 일정이 일치하는지 확인합니다.
1. 예약된 업데이트 옆에 있는 편집 작업 을 선택합니다. 데이터는 여전히 위에서 일치해야 합니다.
1. 예정된 날짜를 더 가까운 날짜로 변경합니다. 지금부터 +1년 대신 + 1주 또는 + 1개월로 변경합니다.
1. 변경 사항을 저장하고 날짜가 스테이징 대시보드에 업데이트되었는지 확인합니다.
1. cron 작업이 실행될 때까지 기다립니다.
1. 예약된 변경 내용에서 다시 편집 을 클릭하고 가격을 확인합니다.

<u>예상 결과</u>:

가격은 1.99입니다.

<u>실제 결과</u>:

가격은 9.99입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
