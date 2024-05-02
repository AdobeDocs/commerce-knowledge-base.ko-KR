---
title: 'MDVA-40311: 사용자 지정 관리 경로가 구성된 경우 Admin에 로그인한 후 "보안 또는 양식 키가 잘못됨" 오류 발생'
description: '''MDVA-40311 패치는 관리자 사용자에게 오류 메시지가 표시되는 문제를 해결합니다. *잘못된 보안 또는 양식 키. 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후* 페이지를 새로 고치십시오. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40311입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정될 예정입니다."'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: 사용자 지정 관리 경로가 구성된 경우 Admin에 로그인한 후 &quot;보안 또는 양식 키가 잘못됨&quot; 오류 발생

MDVA-40311 패치는 관리자 사용자에게 오류 메시지가 표시되는 문제를 해결합니다. *보안 또는 양식 키가 잘못되었습니다. 페이지를 새로 고치십시오.*: 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치되었습니다. 패치 ID는 MDVA-40311입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 사용자에게 다음 오류 메시지가 표시됩니다. *보안 또는 양식 키가 잘못되었습니다. 페이지를 새로 고치십시오.*: 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후.

<u>재현 단계</u>:

* 유효한 사용자 이름과 암호를 사용하여 관리자로 로그인합니다.

<u>예상 결과</u>:

사용자는 오류 메시지 없이 로그인할 수 있습니다.

<u>실제 결과</u>:

*보안 또는 양식 키가 잘못되었습니다. 페이지를 새로 고치십시오.* 오류 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
