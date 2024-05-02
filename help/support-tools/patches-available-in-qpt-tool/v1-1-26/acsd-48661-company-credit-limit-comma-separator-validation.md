---
title: 'ACSD-48661: 회사 크레딧 제한 쉼표 구분 기호 유효성 검사 문제'
description: ACSD-48661 패치를 적용하여 회사 크레딧 제한이 999보다 큰 경우 쉼표 구분 기호로 인해 유효성 검사 오류로 인해 회사가 저장되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: 회사 크레딧 제한 쉼표 구분 기호 유효성 검사 문제

ACSD-48661 패치는 회사 크레딧 제한이 999보다 큰 경우 쉼표 구분 기호로 인해 유효성 검사 오류로 인해 회사가 저장되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치되었습니다. 패치 ID는 ACSD-48661입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사 신용 한도가 999보다 큰 경우 쉼표 구분 기호는 검증 오류로 인해 회사가 저장되지 않도록 합니다.

<u>재현 단계</u>:

1. 에서 회사 기능 활성화 **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. 회사를 만들고 아래의 신용 한도가 999보다 큼 **[!UICONTROL Company Credit]** 탭.
1. 회사를 구하십시오.
1. 회사를 편집하고 다시 저장해 보십시오.

<u>예상 결과</u>:

당신은 신용 한도를 정하지 않고도 회사를 살릴 수 있다. 금액 및 가격에 대한 입력 필드에 쉼표가 지원되지 않습니다.

<u>실제 결과</u>:

의 유효성 검사 오류로 인해 회사를 저장할 수 없습니다. *[!UICONTROL Credit Limit]* 필드. Adobe Commerce은 크레딧 제한에 쉼표 구분 기호를 자동으로 추가합니다. [!UICONTROL Credit Limit] 필드는 쉼표를 허용하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
