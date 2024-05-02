---
title: "ACSD-46541: 주문 항목이 삭제된 경우 관리자가 대변 메모를 만들 수 없음"
description: ACSD-46541 패치를 적용하여 제품이 삭제되면 Adobe Commerce 관리자에서 대변 메모를 만들 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: ff3f8f21-76c1-41b5-bf02-349403a46fc1
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46541: 주문 항목을 삭제한 경우 관리자가 대변 메모를 만들 수 없음

ACSD-46541 패치는 주문 항목이 삭제될 경우 관리자가 대변 메모를 작성할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21이 설치되었습니다. 패치 ID는 ACSD-46541입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 삭제되면 Commerce 관리자에서 대변 메모를 만들 수 없습니다.

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다.
1. 주문을 만듭니다.
1. 주문에 대한 송장을 발행합니다.
1. 주문에서 제품을 삭제합니다.
1. 을(를) 클릭합니다 **[!UICONTROL Credit Memo]** 주문 편집 페이지에 연결합니다.
1. 클릭 **[!UICONTROL Refund Offline]** 대변 메모를 생성합니다.

<u>예상 결과</u>:

대변 메모가 정상적으로 생성되었습니다.

<u>실제 결과</u>:

다음 _요청한 SKU가 포함된 다음 제품을 찾을 수 없습니다. SKU001_ 오류가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
