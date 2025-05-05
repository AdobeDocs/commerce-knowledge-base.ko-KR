---
title: 'MDVA-33606: 계층에 할당된 CMS 페이지를 저장할 때 사용자에게 오류가 발생했습니다.'
description: MDVA-33606 패치는 계층 트리에 할당된 CMS 페이지를 저장할 때 사용자에게 *고유 제한 위반 발견* 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-33606입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: 계층에 할당된 CMS 페이지를 저장할 때 사용자에게 오류가 발생했습니다.

MDVA-33606 패치는 계층 트리에 할당된 CMS 페이지를 저장할 때 사용자에게 *고유 제약 조건 위반이 발견되었습니다* 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-33606입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1-2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

계층 트리에 할당된 CMS 페이지를 저장하려고 하면 다음과 같은 오류 메시지가 표시됩니다. *고유 제한 위반 발견*.

<u>재현 단계</u>:

1. 새 CMS 페이지를 만듭니다. 범위를 모든 스토어 조회수로 설정합니다. CMS 페이지 1입니다.
1. 새 스토어 뷰를 만듭니다. 스토어 보기 2입니다.
1. **컨텐츠** > **계층 구조** > 계층 구조 트리에 CMS 페이지 1 추가 로 이동합니다.
1. 범위를 스토어 뷰 2로 변경합니다.
   * &quot;상위 노드 계층 사용&quot;을 선택 취소합니다.
   * CMS 페이지 1을 이 범위에 추가하고 저장합니다.
1. 이제 범위를 기본 스토어 보기로 변경합니다.
   * &quot;상위 노드 계층 사용&quot;을 선택 취소합니다.
   * CMS 페이지 1을 이 범위에 추가하고 저장합니다.
1. **콘텐츠** > **페이지** > **새 페이지 추가**(으)로 이동합니다.
   * 페이지 제목을 페이지 2로 지정합니다.
   * 웹 사이트의 페이지 섹션에서 모든 스토어 보기 수 및 두 스토어 보기 수(기본 스토어 보기 및 스토어 보기 2)에 지정한 다음 **페이지 저장**&#x200B;을 클릭합니다.
1. CMS 편집 페이지에서 계층 탭을 엽니다.
   * 페이지 2를 저장 보기 2 노드, 기본 노드 및 모든 웹 사이트 노드에 할당합니다.

<u>예상 결과</u>:

오류 없이 CMS 페이지를 세 노드 모두에 할당할 수 있습니다.

<u>실제 결과</u>:

다음 오류가 발생했습니다. *UNIQUE 제약 조건 위반이 발견되었습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
