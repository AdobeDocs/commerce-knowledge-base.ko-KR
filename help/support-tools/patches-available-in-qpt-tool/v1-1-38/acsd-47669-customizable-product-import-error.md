---
title: 'ACSD-47669: 사용자 지정 가능한 옵션이 있는 제품을 가져올 때 내부 서버 오류 발생'
description: ACSD-47669 패치를 적용하여 사용자 지정 가능한 옵션이 있는 제품을 가져오는 동안 내부 서버 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669: 사용자 지정 가능한 옵션이 있는 제품을 가져올 때 내부 서버 오류 발생

ACSD-47669 패치는 사용자 지정 가능한 옵션을 사용하여 제품을 가져오는 동안 내부 서버 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.38이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47669입니다. 이 문제는 Adobe Commerce 2.4.6에서 이미 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 가능한 옵션이 있는 제품을 가져올 때 내부 서버 오류가 발생합니다.

<u>재현 단계</u>:

1. 추가 스토어 뷰를 만듭니다. 2개의 스토어 조회수(예: en, UK)가 있는지 확인합니다.
1. 두 개의 간단한 제품(예: prod1 및 prod2)을 생성합니다.
1. 각 스토어 보기의 제품과 **모든 스토어 보기** 범위의 두 제품에 대한 사용자 지정 옵션을 추가하는 csv 파일을 준비하십시오. 이 csv 파일을 가져옵니다.
1. 두 개의 레코드가 포함된 다른 csv 파일을 준비합니다. 첫 번째 레코드는 영국 저장소 보기 범위에 대한 &#39;prod1&#39;의 사용자 지정 옵션을 업데이트하는 것이고 두 번째 레코드는 **모든 저장소 보기** 범위에 대한 &#39;prod2&#39;의 사용자 지정 옵션을 업데이트하는 것입니다. 이 두 번째 csv 파일을 가져옵니다.

<u>예상 결과</u>:

오류 없이 옵션을 사용자 지정할 수 있어야 합니다.

<u>실제 결과</u>:

무결성 제약 조건 위반 오류가 발생했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
