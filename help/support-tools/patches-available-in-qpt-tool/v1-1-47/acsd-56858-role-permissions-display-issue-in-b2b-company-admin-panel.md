---
title: 'ACSD-56858: B2B 회사 관리자의 역할 권한 불일치'
description: ACSD-56858 패치를 적용하여 B2B 환경에서 제한된 회사 관리자에 대해 역할 권한이 잘못 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: B2B 회사 관리자의 역할 권한 불일치

ACSD-56858 패치는 B2B 환경에서 제한된 회사 관리자에 대한 역할 권한이 잘못 표시되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.47이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56858입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

B2B 환경에서 제한된 회사 관리자의 역할 권한이 잘못 표시됩니다.

<u>재현 단계</u>:

1. 회사 설정, 회사 관리자 및 회사 사용자 추가부터 시작합니다.
1. 상점 첫 화면에서 회사 관리자로 로그인하고 다양한 사용자를 위한 다양한 역할을 만듭니다.
1. 필요에 따라 이러한 역할을 할당하십시오(예: 일부 작업에 대한 액세스 제한). 다른 작업에 대한 전체 액세스를 허용합니다.
1. 회사 관리자가 아닌 사용자에게 전체 액세스 권한을 가지고 이러한 역할을 할당합니다.
1. 회사 관리자가 아닌 사용자(예: company_manager)에 로그인합니다.
1. **[!UICONTROL Roles and permission]**(으)로 이동하여 역할을 편집합니다.
1. 표시된 권한이 해당 역할 ID에 대해 회사 데이터베이스에 설정된 권한과 일치하지 않습니다.

<u>예상 결과</u>:

회사 관리자가 아닌 사용자에게 역할과 권한이 올바르게 표시됩니다.

<u>실제 결과</u>:

회사 관리자가 아닌 사용자의 경우 권한 테이블의 데이터베이스 레코드에 따라 역할이 올바르게 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
