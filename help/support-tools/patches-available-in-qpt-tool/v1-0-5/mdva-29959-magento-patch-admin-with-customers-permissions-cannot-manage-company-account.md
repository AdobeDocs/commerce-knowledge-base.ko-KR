---
title: 'MDVA-29959 패치: "고객" 권한이 있는 관리자가 회사 계정을 관리할 수 없음'
description: '[Quality Patches Tool(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 도구 버전 1.0.5에서 사용할 수 있는 MDVA-29959 패치는 "고객" ACL에 대한 모든 권한을 가진 제한된 관리자가 회사를 관리(회사 추가 또는 삭제)할 수 없는 문제를 해결합니다. Adobe Commerce 2.3.4용 B2B에서 문제가 해결되었습니다.'
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# MDVA-29959 패치: &quot;Customers&quot; 권한이 있는 관리자가 회사 계정을 관리할 수 없음

[품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 도구 버전 1.0.5에서 사용할 수 있는 MDVA-29959 패치는 &quot;고객&quot; ACL에 대한 모든 권한을 가진 제한된 관리자가 회사를 관리(회사 추가 또는 삭제)할 수 없는 문제를 해결합니다. Adobe Commerce 2.3.4용 B2B에서 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

클라우드 인프라 2.3.0-2.3.3-p1의 Adobe Commerce용 B2B.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

&quot;고객&quot; ACL에 대한 모든 권한이 있는 관리자는 회사를 관리(회사 추가 또는 삭제)할 수 없습니다.

<u>재현 단계</u>

1. Commerce 관리자에서 새 관리자 역할을 만들고 사용자를 해당 역할에 할당합니다.
1. 역할에 &quot;고객&quot; 리소스만 할당합니다.
1. 이 역할을 가진 사용자로 로그인합니다.
1. 회사 계정을 삭제해 보십시오.

<u>예상 결과:</u>

회사 계정이 정상적으로 삭제되었습니다.

<u>실제 결과:</u>

회사 계정을 삭제할 수 없습니다. *을(를) 가져옵니다. 죄송합니다. 이 콘텐츠를 볼 수 있는 권한이 필요합니다.* 오류 메시지입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
