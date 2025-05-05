---
title: 'ACSD-47988: 페이지 빌더 제품 설명의 제품 내보내기 트림 HTML 태그'
description: ACSD-47988 패치를 적용하여 제품 내보내기가 페이지 빌더 제품 설명의 HTML 태그를 트리밍하는 Adobe Commerce 문제를 해결합니다.
exl-id: 96c45ca8-f526-4876-8f2c-39bce07f86eb
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-47988: 페이지 빌더 제품 설명의 제품 내보내기 트림 HTML 태그

ACSD-47988 패치는 제품 내보내기가 페이지 빌더 제품 설명의 HTML 태그를 트리밍하는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47988입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 내보내기는 페이지 빌더 제품 설명의 HTML 태그를 트리밍합니다.

<u>재현 단계</u>:

1. 설명에 일부 HTML이 있는 제품을 만듭니다. 페이지 빌더 HTML 요소를 사용하여 HTML 태그를 삽입합니다.
1. Adobe Commerce의 가져오기/내보내기 기능을 사용하여 제품을 내보냅니다.
1. 내보낸 CSV를 가져옵니다.
1. 제품을 열고 설명 아래의 HTML 요소를 확인합니다.

<u>예상 결과</u>:

HTML 태그는 동일한 콘텐츠를 가져온 후에도 제품 설명에 유지됩니다.

<u>실제 결과</u>:

HTML 태그는 가져온 후 제거됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
