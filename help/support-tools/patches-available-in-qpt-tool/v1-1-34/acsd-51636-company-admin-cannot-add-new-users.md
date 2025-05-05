---
title: "ACSD-51636: 회사 관리자가 고객 계정 섹션에서 새 사용자를 추가할 수 없음"
description: ACSD-51636 패치를 적용하여 회사 관리자가 필요한 모든 역할 및 권한을 가지고 있음에도 불구하고 고객 계정 섹션에서 새 사용자를 추가할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 78395584-e5d3-414e-859d-a68ce1af5af1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51636: 회사 관리자가 고객 계정 섹션에서 새 사용자를 추가할 수 없음

ACSD-51636 패치는 회사 관리자가 모든 필요한 역할 및 권한을 가지고 있음에도 불구하고 고객 계정 섹션에서 새 사용자를 추가할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51636입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

필요한 모든 역할 및 권한이 있음에도 불구하고 회사 관리자는 고객 계정 섹션에서 새 사용자를 추가할 수 없습니다.

사전 요구 사항:

* B2B 모듈이 설치되었습니다.
* 회사 기능이 활성화되었습니다.

<u>재현 단계</u>:

1. 새 회사를 만듭니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**(으)로 이동합니다.
1. **[!UICONTROL Company Admin]** 형식을 *Customer*(으)로 편집합니다.
1. 고객으로 로그인.
1. **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]**(으)로 이동하여 사용자에 대한 세부 정보를 추가하고 활성화하십시오.
1. 새 사용자를 저장합니다.

<u>예상 결과</u>

관리자는 새 사용자를 추가할 수 있습니다.

<u>실제 결과</u>

* 관리자 사용자에게 오류 메시지: *문제가 발생했습니다*.
* 관리자가 새 고객을 만들 수 없습니다.
* 로그에 다음 오류가 포함되어 있습니다.

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>)을 참조하세요.
