---
title: 'ACSD-46674: 고객 이메일에서 HTML으로 표시되는 이미지 유형의 사용자 지정 옵션'
description: ACSD-46674 패치를 적용하여 이미지 유형의 사용자 지정 옵션이 고객 이메일에 HTML으로 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: 고객 이메일에서 HTML으로 표시되는 이미지 유형의 맞춤형 옵션

ACSD-46674 패치는 이미지 유형의 사용자 지정 옵션이 고객 이메일에서 HTML으로 표시되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21이 설치되었습니다. 패치 ID는 ACSD-46674입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이미지 유형의 사용자 지정 옵션은 고객 이메일에서 HTML으로 표시됩니다.

<u>재현 단계</u>:

1. 사용자 지정 옵션으로 제품을 만듭니다.
   * 옵션 유형: *파일*
   * 호환 가능한 파일 확장명: *png, jpg, gif*
   * 필수 여부: *예*
1. 이미지가 사용자 정의 옵션으로 업로드된 상태로 이 제품을 주문합니다.
1. 2단계에서 생성된 주문에 대한 송장을 생성합니다.
1. 대변 메모를 생성합니다.
1. 모든 확인 이메일을 확인합니다.

<u>예상 결과</u>:

확인 이메일에 업로드된 이미지가 표시됩니다.

<u>실제 결과</u>:

확인 이메일에는 제품 사용자 지정 옵션 이미지 대신 일반 HTML 코드가 포함되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tools] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

에서 사용할 수 있는 다른 패치에 대한 정보 [!DNL QPT], 참조 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
