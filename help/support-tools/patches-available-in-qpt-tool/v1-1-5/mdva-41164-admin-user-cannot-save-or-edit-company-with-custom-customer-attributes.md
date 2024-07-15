---
title: 'MDVA-41164: 사용자 지정 고객 특성으로 회사를 저장하거나 편집할 수 없음'
description: MDVA-41164 패치는 관리자가 파일 또는 모든 유형의 이미지에 대한 사용자 지정 고객 특성을 사용하여 회사를 저장하거나 편집할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41164입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: 사용자 지정 고객 특성을 사용하여 회사를 저장하거나 편집할 수 없음

MDVA-41164 패치는 관리자가 파일 또는 모든 유형의 이미지에 대한 사용자 지정 고객 특성을 사용하여 회사를 저장하거나 편집할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41164입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 사용자는 모든 유형의 파일 또는 이미지에 대한 사용자 정의 고객 속성으로 회사를 저장하거나 편집할 수 없습니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **B2B 기능**&#x200B;에서 회사를 사용하도록 설정하십시오.
1. **스토어** > **특성** > **고객** > **새 특성 추가**&#x200B;에서 고객 특성을 만듭니다.
   * 입력 유형: 파일(첨부 파일)
   * 상점 첫 화면: 예
   * 정렬 순서: 모두
   * 에서 사용할 Forms: 모두 선택
1. **고객** > **회사** > **새 회사 추가**&#x200B;에서 새 회사를 만들고 위에서 만든 새 특성에 대한 파일을 업로드하십시오.

<u>예상 결과</u>:

사용자는 회사 만들기를 완료할 수 있으며 첨부 파일은 오류 없이 업로드됩니다.

<u>실제 결과</u>:

* *파일을 저장하는 동안 문제가 발생했습니다.*
* 예외 로그에는 다음과 같은 레코드가 포함되어 있습니다.

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
