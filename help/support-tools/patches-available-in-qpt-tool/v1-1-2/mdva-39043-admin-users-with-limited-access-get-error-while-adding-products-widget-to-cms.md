---
title: 'MDVA-39043: 관리자 사용자가 CMS 페이지에 위젯을 추가하는 동안 오류가 발생했습니다.'
description: MDVA-39043 패치는 CMS 페이지에 "제품" 위젯을 추가하는 동안 액세스 권한이 제한된 관리 사용자가 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39043입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: 관리자가 CMS 페이지에 위젯을 추가하는 동안 오류가 발생했습니다.

MDVA-39043 패치는 CMS 페이지에 &quot;제품&quot; 위젯을 추가하는 동안 액세스 권한이 제한된 관리 사용자가 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39043입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.4 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

액세스 권한이 제한된 관리자는 CMS 페이지에 &quot;제품&quot; 위젯을 추가하는 동안 오류가 발생합니다.

<u>재현 단계</u>:

1. 콘텐츠 편집 전용 액세스 권한이 있는 관리자를 사용하여 백엔드에 로그인합니다.
1. **컨텐츠** > **페이지**(으)로 이동합니다.
1. 편집할 페이지를 엽니다.
1. **페이지 빌더**&#x200B;로 콘텐츠를 편집하세요.
1. **콘텐츠 추가** 섹션에서 **제품** 위젯을 추가합니다.
1. **제품** 위젯에서 **구성**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

오류가 표시되지 않습니다.

<u>실제 결과</u>:

다음 오류 메시지가 수신됩니다.

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
