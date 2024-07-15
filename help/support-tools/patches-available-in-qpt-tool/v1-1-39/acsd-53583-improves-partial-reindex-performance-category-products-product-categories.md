---
title: 'ACSD-53583: [!UICONTROL Category Products] 및 [!UICONTROL Product Categories] 인덱서에 대한 부분 색인 재지정 성능 개선'
description: ACSD-53585 패치를 적용하여 범주 제품 및 제품 범주 인덱서에 대한 부분 색인 재지정 성능을 개선합니다.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: 카테고리 제품 및 제품 카테고리 인덱서에 대한 부분 색인 재지정 성능 개선

ACSD-53583 패치는 *카테고리 제품* 및 *제품 카테고리* 인덱서의 부분 색인 재지정 성능을 개선합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.39가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53583입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3
* [!DNL Live Search] 모듈과 호환되지 않습니다. [!DNL Live Search] 설치에 이 패치를 적용하려면 추가 ACSD-55719 패치를 요청하십시오.

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

부분 색인 재지정은 전체 색인 재지정보다 시간이 더 걸립니다.

<u>재현 단계</u>:

1. 모든 인덱서를 *일정별 업데이트*(으)로 설정합니다.
1. [!DNL Performance Toolkit](중간 프로필)을 사용하여 데이터를 생성합니다.
1. 인덱스 백로그에 있고 모든 인덱스가 유휴 상태가 되도록 모든 제품 및 범주를 변경합니다.
1. *범주 제품* 및 *제품 범주* 인덱서에 대해 부분 리인덱싱을 수행합니다.

<u>예상 결과</u>:

부분 리인덱스는 제품당 한 번 호출되며 모든 제품과 카테고리가 변경되었기 때문에 전체 리인덱스와 거의 동일한 시간이 소요된다.

<u>실제 결과</u>:

부분 리인덱스는 제품당 여러 번 호출되며 전체 리인덱싱보다 시간이 더 많이 소요된다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
