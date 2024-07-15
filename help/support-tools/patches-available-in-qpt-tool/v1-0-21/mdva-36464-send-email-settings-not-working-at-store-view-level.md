---
title: 'MDVA-36464: 스토어 보기 수준에서 이메일 설정 전송이 작동하지 않음'
description: MDVA-36464 패치는 스토어-보기 수준에서 이메일 전송 설정이 작동하지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36464입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464: 스토어 보기 수준에서 이메일 설정 전송이 작동하지 않음

MDVA-36464 패치는 스토어-보기 수준에서 이메일 전송 설정이 작동하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-36464입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.0-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소:</u>

깨끗한 Adobe Commerce을 설치합니다.

<u>재현 단계</u>:

1. 추가 웹 사이트, 스토어 및 스토어 보기를 만듭니다. 이 예제에서 두 번째 웹 사이트는 *website2*&#x200B;입니다.
1. **스토어** > **구성** > **고급** > **시스템** > **메일 전송 설정**&#x200B;에서 전역 수준에서 **전자 메일 알림**&#x200B;을 사용하지 않도록 설정합니다.
1. *웹 사이트2* 수준에서 **전자 메일 알림**&#x200B;을 사용하도록 설정합니다(**전자 메일 통신 사용 안 함** = *아니요*).
1. [관리]에서 새 사용자를 만들어 *website2*&#x200B;에 할당합니다.
1. 관리자의 고객 편집 페이지에서 4단계에서 위에서 만든 고객에 대해 **암호 재설정**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

두 번째 웹 사이트(예: *웹 사이트2*)에 대해 **전자 메일 통신 사용 안 함** = *아니요*&#x200B;이므로 **시작 전자 메일**&#x200B;과(와) **암호 재설정 전자 메일**&#x200B;이 모두 예상대로 전송됩니다.

<u>실제 결과</u>:

* 새 고객을 만든 후 **환영 전자 메일**&#x200B;이 트리거되지 않습니다.
* **암호 재설정 전자 메일**&#x200B;이 트리거되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
