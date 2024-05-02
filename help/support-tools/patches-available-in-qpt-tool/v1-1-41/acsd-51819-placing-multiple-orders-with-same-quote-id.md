---
title: 'ACSD-51819: 단일 견적 ID로 여러 주문 넣기'
description: ACSD-51819 패치를 적용하여 동일한 견적 ID를 통해 여러 주문을 할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Checkout
role: Admin, Developer
exl-id: f217de21-2914-4b84-b596-e9e763669941
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819: 단일 견적 ID로 여러 주문 배치

ACSD-51819 패치는 동일한 견적 ID를 통해 여러 주문을 할 수 있는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41이 설치되었습니다. 패치 ID는 ACSD-51819입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 견적 ID로 여러 주문을 할 수 있습니다.

<u>재현 단계</u>:

1. 사용자로 로그인
1. 장바구니에 항목을 추가하고 체크아웃을 진행합니다.
1. 결제 방법을 선택하되 **[!UICONTROL Place Order]** 단추를 클릭합니다.
1. 다른 브라우저에서 동일한 계정에 로그인합니다.
1. 을(를) 클릭하지 않고 동일한 항목으로 체크아웃을 진행합니다. **[!UICONTROL Place Order]** 단추를 클릭합니다.
1. 을(를) 클릭합니다 **[!UICONTROL Place Order]** 두 시스템의 버튼을 동시에 클릭합니다.
1. 두 브라우저에서 수행한 주문의 유효성을 확인합니다.

<u>예상 결과</u>:

한 브라우저에서 수행한 첫 번째 주문만 성공적으로 처리됩니다.

<u>실제 결과</u>:

두 브라우저 모두에서 주문이 완료되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
