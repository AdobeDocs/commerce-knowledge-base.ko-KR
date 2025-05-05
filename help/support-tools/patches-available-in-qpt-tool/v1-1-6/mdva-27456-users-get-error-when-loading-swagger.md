---
title: 'MDVA-27456: Swagger를 로드할 때 오류가 발생합니다.'
description: MDVA-27456 패치는 사용자가 Swagger를 로드하려고 할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-27456입니다. 이 문제는 Adobe Commerce 2.3.7에서 해결되었습니다.
exl-id: e331595f-a94b-4070-803a-60f559735b29
feature: Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# MDVA-27456: Swagger를 로드할 때 오류가 발생합니다.

MDVA-27456 패치는 사용자가 Swagger를 로드하려고 할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-27456입니다. 이 문제는 Adobe Commerce 2.3.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.3.5-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Swagger를 로드할 때 오류가 발생합니다.

<u>재현 단계</u>:

`../swagger.`(으)로 이동

<u>예상 결과</u>:

Swagger가 오류 없이 로드됩니다.

<u>실제 결과</u>:

사용자에게 *API 정의를 로드하지 못했습니다* 오류가 표시됩니다. 오류 로그에 포함되는 사항:

*report.CRITICAL: 보고서 ID: webapi-5ea9c6da19cb1; 메시지: &quot;\DateTime&quot; 매개 변수 유형이 잘못되었습니다. 매개 변수를 확인하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
