---
title: 'MDVA-37364: 날짜 유형의 사용자 지정 고객 특성이 그리드 UI를 나눕니다.'
description: MDVA-37364 패치는 날짜 유형의 사용자 지정 고객 특성이 고객 그리드 UI를 손상하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37364입니다. 이 문제는 Adobe Commerce 버전 2.4.4에서 수정됩니다.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: 날짜 유형의 사용자 지정 고객 특성이 그리드 UI를 나눕니다.

MDVA-37364 패치는 날짜 유형의 사용자 지정 고객 특성이 고객 그리드 UI를 손상하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37364입니다. 이 문제는 Adobe Commerce 버전 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0-2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

날짜 유형의 사용자 지정 고객 속성은 고객 그리드 UI를 중단합니다.

<u>재현 단계</u>:

1. 날짜 유형으로 사용자 지정 속성을 만듭니다.
   * **스토어** > **특성** > **특성 추가**(으)로 이동합니다.
   * 입력 유형을 날짜로 설정합니다.
   * 열에 추가 옵션을 예로 설정합니다.
   * 속성을 저장합니다.
1. **관리자** > **고객** > **모든 고객**(으)로 이동합니다.
   * 열 옵션에서 새로 추가된 사용자 지정 속성을 그리드에 추가합니다.
1. 고객을 생성/편집하고 생성된 사용자 지정 날짜 속성 필드의 값을 설정합니다.
1. 캐시를 저장, 다시 인덱싱 및 지웁니다.
1. **고객** > **모든 고객**&#x200B;으로 이동합니다.
   * 고객 그리드를 확인합니다.

<u>예상 결과</u>:

관리자 고객 그리드는 고객 그리드 UI를 중단하지 않고 새 날짜 사용자 지정 속성을 포함한 모든 데이터를 표시합니다.

<u>실제 결과</u>:

관리자 고객 그리드 UI가 손상되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
