---
title: 'ACSD-51291: 제한된 관리자는 여러 웹 사이트에 할당된 제품에 이미지/비디오를 추가할 수 있습니다.'
description: ACSD-51291 패치를 적용하여 한 웹 사이트에 대한 액세스 권한이 있는 제한된 관리자가 여러 웹 사이트에 할당된 제품에 이미지/비디오를 추가할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: 제한된 관리자는 여러 웹 사이트에 할당된 제품에 이미지/비디오를 추가할 수 있습니다.

ACSD-51291 패치는 한 웹 사이트에 대한 액세스 권한이 있는 제한된 관리자가 여러 웹 사이트에 할당된 제품에 이미지/비디오를 추가할 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51291입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

한 웹 사이트에 대한 액세스 권한이 있는 제한된 관리자는 여러 웹 사이트에 할당된 제품에 이미지/비디오를 추가할 수 있습니다.

<u>재현 단계</u>

1. 관리자로 로그인합니다.
1. 두 번째 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 두 번째 웹 사이트, 스토어 및 스토어 보기에 대한 리소스만 있는 두 번째 관리자 역할을 만듭니다.
1. 두 번째 관리자를 만들고 새로운 제한된 관리자 역할에 할당합니다.
1. 새 제품을 만들고 기본 웹 사이트와 새 웹 사이트 모두에 할당합니다.
1. 기본 관리자 프로필에서 로그아웃합니다.
1. 제한된 새 관리자로 로그인합니다.
1. 두 웹 사이트에 할당된 작성된 제품을 편집합니다.
1. **[!UICONTROL Images and Videos]** 탭을 엽니다.

<u>예상 결과</u>:

* 다음 메시지가 표시됩니다.

  *제한된 관리자는 제품이 할당된 모든 웹 사이트에 대한 권한이 있는 경우에만 이미지나 비디오로 작업을 수행할 수 있습니다.*

* **[!UICONTROL Add Video]** 단추가 활성화되어 있지 않습니다.

<u>실제 결과</u>:

제한된 관리자는 제품이 액세스 권한이 없는 웹 사이트에 할당된 경우에도 이미지와 비디오를 추가할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
