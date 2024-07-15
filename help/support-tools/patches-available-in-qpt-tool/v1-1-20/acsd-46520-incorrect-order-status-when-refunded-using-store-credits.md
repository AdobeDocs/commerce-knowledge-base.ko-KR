---
title: 'ACSD-46520: 스토어 크레딧을 사용하여 환불할 때 잘못된 주문 상태'
description: 이 문서에서는 스토어 크레딧을 사용하여 환불할 때 사용자가 잘못된 주문 상태를 얻게 되는 문제에 대한 해결 방법을 제공합니다.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: 스토어 크레딧을 사용하여 환불할 때 잘못된 주문 상태

ACSD-46520 패치는 스토어 크레딧을 사용하여 환불할 때 사용자가 잘못된 주문 상태를 받는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46520입니다. 이 문제는 Adobe Commerce 2.4.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3 및 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스토어 크레딧을 사용하여 환불할 때 사용자는 잘못된 주문 상태를 받습니다.

<u>재현 단계</u>:

1. 상점 첫 화면에서 고객 계정을 만들고 로그인합니다.
1. 관리자로부터 고객에게 스토어 크레딧을 할당합니다. 매장 크레딧이 전체 주문에 적용되어야 합니다.
1. 스토어 크레딧을 사용하여 주문합니다.
1. 주문에 대한 송장을 발행합니다.
1. 주문의 전체 금액을 환불하기 위해 대변 메모를 생성합니다.
**[!UICONTROL Refund to store credit]** 확인란을 선택합니다.
1. 주문 상태를 확인합니다.

<u>예상 결과</u>:

주문 상태는 *마감됨*&#x200B;입니다.

<u>실제 결과</u>:

주문 상태가 올바른 상태가 아닌 *완료*&#x200B;입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 [!DNL Magento Open Source] 온-프레미스: 품질 패치 도구 안내서의 [품질 패치 도구 > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 품질 패치 도구 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하십시오.
