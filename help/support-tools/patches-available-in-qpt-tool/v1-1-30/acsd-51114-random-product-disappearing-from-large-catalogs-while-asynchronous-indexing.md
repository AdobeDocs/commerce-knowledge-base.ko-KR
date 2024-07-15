---
title: 'ACSD-51114: 비동기 인덱싱이 활성화되면 무작위 제품이 큰 카탈로그에서 사라짐'
description: ACSD-51114 패치를 적용하여 Adobe Commerce 문제 해결 비동기 인덱싱이 활성화되면 대규모 카탈로그에서 무작위 제품이 사라짐
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: 비동기 인덱싱이 활성화되면 무작위 제품이 큰 카탈로그에서 사라짐

>[!NOTE]
>
>이 패치는 더 이상 사용되지 않습니다.

ACSD-51114 패치는 비동기 인덱싱이 활성화되면 대규모 카탈로그에서 무작위 제품이 사라지는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51114입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]:패치 검색 페이지]에서 호환성을 확인하십시오.패치 ID를 검색 키워드로 사용하여 패치를 찾으십시오.

## 문제

비동기 인덱싱이 활성화되면 무작위 제품이 큰 카탈로그에서 사라졌습니다.

<u>재현 단계</u>:

1. 10개 제품 세트를 만듭니다.
1. 모든 인덱서를 **[!UICONTROL Update on Save]** 모드로 설정합니다.
1. 카테고리를 만들고 모든 제품을 카테고리에 할당합니다.
1. 모든 제품을 비활성화합니다.
1. 카테고리를 열고 제품이 없는지 확인합니다.
1. 모든 인덱서를 **[!UICONTROL Update on Schedule]** 모드로 설정합니다.
1. `lib/internal/Magento/Framework/Mview/View.php#L31`에서 `DEFAULT_BATCH_SIZE`을(를) 2로 설정합니다.
1. 1st, 9th, 2nd, 5th, 10th, 3rd 순서로 제품을 활성화합니다.
1. cron 명령을 실행합니다.
1. 카테고리를 다시 엽니다.

<u>예상 결과</u>:

활성화된 모든 제품이 표시됩니다.

<u>실제 결과</u>:

활성화된 모든 제품이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
