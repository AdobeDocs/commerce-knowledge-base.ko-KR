---
title: "ACSD-48204: *예/아니요* 속성에 따라 생성된 카탈로그 가격 규칙은 선택한 범위를 고려하지 않습니다."
description: ACSD-48204 패치를 적용하여 *예/아니요* 속성에 따라 생성된 카탈로그 가격 규칙이 선택한 범위를 고려하지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204: *예/아니요* 특성을 기반으로 만들어진 카탈로그 가격 규칙이 선택한 범위를 고려하지 않습니다.

ACSD-48204 패치는 *예/아니요* 특성을 기반으로 만들어진 카탈로그 가격 규칙이 선택한 범위를 고려하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48204입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*예/아니요* 특성을 기준으로 만든 카탈로그 가격 규칙이 선택한 범위를 고려하지 않습니다.

<u>재현 단계</u>:

1. 두 개의 웹 사이트를 만듭니다(기본값 및 W2).
1. *예/아니요* 유형의 제품 특성을 만듭니다.
   * [!UICONTROL Default value] = [!UICONTROL No] 설정
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. 두 가지 변형(V1 및 V2)이 있는 속성을 기반으로 구성 가능한 제품을 만듭니다.
   * 구성 가능한 변형 특성 집합에 *Yes/No* 특성을 추가합니다.
   * 변형(V1) 중 하나에 대해 기본이 아닌 웹 사이트(W2)에서 값을 *[!UICONTROL Yes]*(으)로 설정합니다.
1. 카탈로그 규칙 만들기:
   * 두 웹 사이트에 적용
   * 조건: *예/아니요* 특성 값은 *[!UICONTROL Yes]*&#x200B;입니다.
   * 할인 = 50%
1. 기본이 아닌 웹 사이트(W2)에서 구성 가능한 제품을 엽니다.
1. V1 변형에 50% 할인이 적용되었는지 확인합니다.
1. Adobe Commerce 관리자에서 V1 변형을 엽니다.
   * 기본 웹 사이트로 전환
   * 변경하지 않고 제품 저장
1. 구성 가능한 제품 상점 첫 페이지를 새로 고칩니다.

<u>예상 결과</u>:

V1 변동은 변동사항이 없어 여전히 50% 할인이 적용됩니다.

<u>실제 결과</u>:

할인이 사라집니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
