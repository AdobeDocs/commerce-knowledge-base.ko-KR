---
title: 'ACSD-54472: 거부된 회사의 고객은 여전히 인증할 수 있습니다'
description: ACSD-54472 패치를 적용하여 거부된 회사의 고객이 계속 인증할 수 있고 거부된 및 거부된 회사의 고객이 여전히 주문을 할 수 있는 Adobe Commerce 문제를 수정합니다.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: 거부된 회사의 고객은 여전히 인증할 수 있습니다

ACSD-54472 패치는 거부된 회사의 고객이 계속 인증할 수 있고, 차단되고 거부된 회사의 고객이 여전히 주문을 할 수 있는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54472입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

거부된 회사의 고객은 계속 인증할 수 있고, 거부된 및 거부된 회사의 고객은 여전히 주문을 할 수 있습니다.

<u>재현 단계</u>:

1. 회사를 만듭니다.
1. [!DNL GraphQL]을(를) 통해 장바구니에 제품을 추가합니다.
1. 회사 상태를 *차단됨*(으)로 변경합니다.
1. 주문을 하고 협상 가능한 견적을 만들려면 [!DNL GraphQL] 요청을 보냅니다.
1. 회사 상태를 *거부됨*(으)로 변경합니다.
1. 회사의 사용자 인증 토큰을 가져오려면 [!DNL GraphQL] 요청을 전송하십시오.
1. 고객 상태를 *비활성*(으)로 설정합니다.
1. 회사의 사용자 인증 토큰을 가져오려면 [!DNL GraphQL] 요청을 전송하십시오.

<u>예상 결과</u>:

* *차단됨* 회사의 사용자가 주문 및 협상 가능 견적을 가져오지 않았습니다.
* *거부됨* 회사의 사용자에 대한 인증 토큰을 가져올 수 없습니다.
* *비활성* 고객에 대한 인증 토큰을 가져올 수 없습니다.

<u>실제 결과</u>:

* 주문 및 협상 가능 견적은 *차단됨* 회사의 사용자가 지정합니다.
* *거부됨* 회사의 사용자에 대한 인증 토큰을 얻었습니다.
* *비활성* 고객에 대한 인증 토큰을 얻었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
