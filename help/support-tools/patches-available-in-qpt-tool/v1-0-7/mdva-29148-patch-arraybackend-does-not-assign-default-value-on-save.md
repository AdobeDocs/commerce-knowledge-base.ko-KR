---
title: 'MDVA-29148: ArrayBackend가 저장 시 기본값을 할당하지 않음'
description: MDVA-29148 패치는 저장 시 '\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend'가 기본값을 할당하지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148: ArrayBackend가 저장 시 기본값을 할당하지 않습니다.

MDVA-29148 패치는 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend`에서 저장 시 기본값을 할당하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.3-p1.

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

가져오기 스크립트 또는 REST API를 통해 제품을 만들 때 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 백엔드 모델을 사용하고 기본값이 있는 특성에 기본값이 할당되지 않습니다.

<u>재현 단계</u>:

1. `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 백 엔드 모델과 비어 있지 않은 기본값을 사용하는 새 전역 특성을 만드십시오.
1. REST API를 사용하여 새 제품을 만듭니다.
1. REST API에서 새 제품을 가져오고 속성이 제품의 사용자 지정 속성에 없는지 확인합니다.

<u>예상 결과</u>:

사용자 지정 속성 기본값이 제품 속성에 저장되었습니다.

<u>실제 결과</u>:

사용자 지정 속성 기본값이 제품 속성에 저장되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
