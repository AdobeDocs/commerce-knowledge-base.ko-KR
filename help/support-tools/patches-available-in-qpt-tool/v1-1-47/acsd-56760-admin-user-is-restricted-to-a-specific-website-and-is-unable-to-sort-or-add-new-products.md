---
title: 'ACSD-56760: 관리자 사용자가 특정 웹 사이트로 제한되어 새 제품을 정렬 또는 추가할 수 없음'
description: ACSD-56760 패치를 적용하여 특정 웹 사이트로 제한되어 있고 웹 스토어에 자체 루트 카테고리가 있는 경우 카테고리 내에 새 제품을 정렬하거나 추가할 수 없는 Adobe Commerce 문제를 해결합니다.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: 관리자 사용자가 특정 웹 사이트로 제한되어 새 제품을 정렬 또는 추가할 수 없음

ACSD-56760 패치는 특정 웹 사이트로 제한되어 있고 웹 스토어에 자체 루트 범주가 있는 경우 범주 내에서 새 제품을 정렬 또는 추가할 수 없는 관리 사용자 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.47이 설치되었습니다. 패치 ID는 ACSD-56760입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 웹 사이트로 제한되어 있으며 웹 스토어에 자체 루트 카테고리가 있는 경우 카테고리 내에서 새 제품을 정렬하거나 추가할 수 없는 관리자 사용자입니다.

<u>재현 단계</u>:

1. 만들기 *2* 웹 사이트.
1. 만들기 **[!UICONTROL restricted admin user]** 에 대한 액세스 권한만 포함 *1* 웹 사이트입니다.
1. 다음으로 로그인 **[!UICONTROL restricted admin user]** 범주의 제품 위치를 변경해 보십시오.

*사례 1*:

* *2* 상점.
* *2* 루트 범주, 각 웹 사이트가 자체 범주 루트에 할당됩니다.

*사례 2*:

* *2* 상점.
* 전용 *1* 루트 카테고리가 두 웹 사이트에 할당됩니다.

<u>예상 결과</u>:

* *사례 1*: 제한된 관리자는 사용 가능한 범주 내에서 제품을 정렬할 수 있어야 합니다.
* *사례 2*: 제한된 관리자는 사용 가능한 범주 내에서 제품을 정렬할 수 없습니다. 이는 제한된 저장소에도 영향을 미치기 때문입니다.

<u>실제 결과</u>:

* *사례 1*: 제한된 관리자는 사용 가능한 범주 내에서 제품을 정렬할 수 없습니다.
* *사례 2*: 제한된 관리자는 사용 가능한 범주 내에서 제품을 정렬하여 제한된 스토어에 영향을 줄 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
