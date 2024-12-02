---
title: 'MDVA-39384: 회사 사용자에 대한 사용자 지정 고객 특성을 저장할 수 없습니다.'
description: MDVA-39384 패치는 회사 사용자에 대한 사용자 지정 고객 특성이 저장되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39384입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384: 회사 사용자에 대한 사용자 지정 고객 특성을 저장할 수 없습니다.

MDVA-39384 패치는 회사 사용자에 대한 사용자 지정 고객 특성이 저장되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39384입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사 사용자에 대한 사용자 지정 고객 속성이 저장되지 않았습니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. **스토어** > 설정 > **구성** > **B2B 기능**(으)로 이동하여 **회사 사용**&#x200B;을 예로 설정합니다.
1. 사용자 지정 고객 속성을 만듭니다.
   * 필수 값: 예(선택 사항, 검증 오류가 표시되도록 활성화).
   * 상점 앞에 표시: 예.
   * 에서 사용할 Forms: 목록에서 모두 사용할 수 있습니다.
1. 회사를 만들고 회사 관리자로 로그인합니다.
1. 계정의 회사 구조로 이동합니다.
1. **사용자 추가** 링크를 클릭합니다.
1. 사용자 지정 특성을 포함하여 양식을 채웁니다.
1. **저장**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

사용자 지정 속성 값은 새 회사 사용자와 함께 저장됩니다.

<u>실제 결과</u>:

사용자 지정 속성 값은 새 회사 사용자와 함께 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
