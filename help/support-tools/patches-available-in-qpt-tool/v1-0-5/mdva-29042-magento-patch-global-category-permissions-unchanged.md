---
title: 'MDVA-29042: 전역 범주 권한이 변경되지 않음'
description: MDVA-29042 패치는 Commerce 관리자의 공유 카탈로그에 새 제품이 추가된 후 카탈로그 권한이 자동으로 "*Allow*"로 변경되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우 사용할 수 있습니다. Adobe Commerce 2.3.6에서 B2B 확장 기능으로 문제가 해결되었습니다.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042: 전역 범주 권한이 변경되지 않음

MDVA-29042 패치는 Commerce 관리자의 공유 카탈로그에 새 제품을 추가한 후 카탈로그 권한이 자동으로 &quot;*허용*&quot;(으)로 변경된 문제를 해결했습니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우에 사용할 수 있습니다. Adobe Commerce 2.3.6에서 B2B 확장 기능으로 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

B2B 확장이 있는 Adobe Commerce(모든 배포 방법) 2.3.3에서 2.3.4-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Commerce 관리자의 전역 범주 권한에서 고객 그룹을 선택 취소해도 해당 고객 그룹은 범주 권한 내에서 자동으로 &quot;*Deny*&quot;(으)로 설정되지 않습니다.

<u>필수 구성 요소</u>:

* 다음에 대한 **스토어** > **구성** > **카탈로그** > **카탈로그** > **범주 권한**&#x200B;에서 고객 그룹이 정의되고 선택된 B2B 인스턴스:
   * **범주 검색 허용**
   * **제품 가격 표시**
   * **장바구니에 추가 허용**
* 각 **Category**&#x200B;에서 고객 그룹은 다음에 대해 &quot;*Allow*&quot;(으)로 정의됩니다.
   * **범주 검색**
   * **제품 가격 표시**
   * **장바구니에 추가**

<u>재현 단계</u>:

1. Commerce 관리에서 **스토어** > **구성** > **카탈로그** > **카탈로그** > **범주 권한**(으)로 이동하여 다음 위치에서 고객 그룹을 선택 해제합니다.
   * **범주 검색 허용**
   * **제품 가격 표시**
   * **장바구니에 추가 허용**
1. **구성 저장** 단추를 클릭합니다.
1. 인덱서가 실행될 때까지 기다립니다.
1. **카탈로그** > **범주** > **범주 권한**&#x200B;을 참조하세요.

<u>예상 결과</u>:

**범주 권한**&#x200B;은(는) 고객 그룹의 모든 범주에 대해 &quot;*Deny*&quot;(으)로 설정됩니다.

<u>실제 결과</u>:

고객 그룹에 대한 범주 권한은 변경되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.

B2B 회사 기능에 대한 자세한 내용은 개발자 설명서에서 다음 문서를 참조하십시오.

* [B2B 개발자 안내서](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [회사 역할 관리](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B 확장 구성 경로 참조](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
