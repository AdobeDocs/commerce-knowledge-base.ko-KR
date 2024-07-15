---
title: 'MDVA-32739 패치: 비동기 전송이 활성화된 경우 이전 이메일이 전송됨'
description: MDVA-32739 패치는 [비동기 이메일 알림](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications)을 활성화하면 이전 판매 이메일이 전송되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정됩니다.
exl-id: 8cf4ef8a-f2f2-47fb-9f69-0eedcc10ba8b
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-32739 패치: 비동기 전송이 활성화된 경우 이전 이메일이 전송됨

MDVA-32739 패치는 [비동기 전자 메일 알림](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications)을 사용하도록 설정하면 이전 판매 전자 메일이 전송되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정됩니다.

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

1. 비동기 이메일 전송을 비활성화합니다.
1. 주문을 만들고 이메일 전송이 실패하는지 확인합니다.
1. 비동기 전송을 활성화합니다.

<u>예상 결과</u>:

마지막 비동기 전송 업데이트 후에 생성된 주문, 배송, 송장 및 대변 메모에 대해서만 이메일이 발송됩니다.

<u>실제 결과</u>:

이전 이메일은 cronjob을 통해 발송됩니다.

## 수정

이 수정 사항이 패치에 포함되면 Adobe Commerce은 비동기 전송 메서드를 마지막으로 실행한 후 생성된 주문을 선택하고 이러한 주문에 대한 이메일을 전송합니다.

기본적으로 -1일의 오프셋으로 을 선택합니다.

`di.xml`을(를) 수정하여 이 값을 -2일로 변경할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
