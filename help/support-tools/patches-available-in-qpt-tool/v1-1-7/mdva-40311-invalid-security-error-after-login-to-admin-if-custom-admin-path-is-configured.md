---
title: 'MDVA-40311: 사용자 지정 관리 경로가 구성된 경우 Admin에 로그인한 후 "보안 또는 양식 키가 잘못됨" 오류 발생'
description: '''MDVA-40311 패치는 관리자 사용자에게 오류 메시지가 표시되는 문제를 해결합니다. *잘못된 보안 또는 양식 키. 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후* 페이지를 새로 고치십시오. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40311입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정될 예정입니다."'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: 사용자 지정 관리 경로가 구성된 경우 Admin에 로그인한 후 &quot;보안 또는 양식 키가 잘못됨&quot; 오류 발생

MDVA-40311 패치는 관리자 사용자에게 오류 메시지가 표시되는 문제를 해결합니다. *잘못된 보안 또는 양식 키입니다. 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후* 페이지를 새로 고치십시오. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40311입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자가 오류 메시지를 받습니다. *잘못된 보안 또는 양식 키입니다. 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후* 페이지를 새로 고치십시오.

<u>재현 단계</u>:

* 유효한 사용자 이름과 암호를 사용하여 관리자로 로그인합니다.

<u>예상 결과</u>:

사용자는 오류 메시지 없이 로그인할 수 있습니다.

<u>실제 결과</u>:

*보안 또는 양식 키가 잘못되었습니다.* 페이지를 새로 고치십시오. 오류 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
