---
title: 'MDVA-40175: 순서를 변경할 때 라디오 단추가 표시되지 않음'
description: MDVA-40175 패치는 사용자가 순서를 변경하려고 할 때 라디오 단추가 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40175입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175: 순서를 변경할 때 라디오 단추가 표시되지 않음

MDVA-40175 패치는 사용자가 순서를 변경하려고 할 때 라디오 단추가 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40175입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 순서를 변경할 때 결제 및 배송 정보 섹션에 라디오 버튼이 표시되지 않습니다.

<u>필수 구성 요소</u>:

1. 배송 주소와 청구 주소가 있는 고객 계정이 생성됩니다.
1. 단순 제품이 만들어집니다.
1. 여러 게재 방법이 구성됩니다.
1. 하나 이상의 순서가 생성되었습니다.

<u>재현 단계</u>:

1. 관리 패널 > **판매** > **주문**(으)로 이동합니다.
1. 생성된 주문을 선택합니다.
1. **보기** 링크를 클릭합니다.
1. **순서 바꾸기** 단추를 클릭합니다.
1. 페이지를 아래로 스크롤하여 **결제 및 배송 정보** 섹션으로 이동합니다.
1. **배송 방법을 변경하려면 클릭하세요**.

<u>예상 결과</u>:

라디오 단추가 있는 게재 방법 목록이 나타납니다.

<u>실제 결과</u>:

라디오 단추가 없는 게재 방법 목록이 나타납니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
