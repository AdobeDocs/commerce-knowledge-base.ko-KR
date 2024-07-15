---
title: 'ACSD-51102: 카탈로그 규칙이 올바르게 인덱싱되지 않은 많은 제품에 적용됨'
description: ACSD-51102 패치를 적용하여 많은 수의 제품에 적용되는 카탈로그 규칙이 예약된 업데이트에 의해 활성화될 때 올바르게 인덱싱되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102: 카탈로그 규칙이 올바르게 인덱싱되지 않은 많은 제품에 적용됨

ACSD-51102 패치는 예약된 업데이트로 인해 규칙이 활성화될 때 많은 수의 제품에 적용되는 카탈로그 규칙이 올바르게 인덱싱되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51102입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

예약된 업데이트로 인해 규칙이 활성화되면 많은 제품에 적용되는 카탈로그 규칙이 올바르게 색인화되지 않습니다.

사전 요구 사항:

* Cron 작업이 설정되어 매 분마다 실행됩니다.

<u>재현 단계</u>:

1. 카탈로그 규칙을 사용할 수 있을 때 *카탈로그 규칙* 인덱서의 실행 시간을 120초 이상 달성하려면 수천 개의 제품으로 큰 카탈로그를 만드십시오.
2. *활성* 상태가 *아니요*(으)로 설정된 두 개의 카탈로그 규칙을 만듭니다.  예: *테스트 1* 및 *테스트 2*. 각 규칙은 카탈로그의 모든 제품에 영향을 주고 인덱서가 120초 이상 실행되도록 해야 합니다.
3. 인덱서의 상태가 *준비*&#x200B;인지 확인하십시오.
4. 예약된 업데이트를 만들어 이 두 규칙을 활성화합니다. *테스트 2* 일정은 *테스트 1* 직후에 시작해야 합니다. 예를 들어, 1분 차이가 있습니다.
5. 상점에서 제품 가격을 확인하십시오.

<u>예상 결과</u>

두 규칙의 할인이 적용됩니다.

<u>실제 결과</u>

첫 번째 규칙 할인만 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)을 참조하세요.
