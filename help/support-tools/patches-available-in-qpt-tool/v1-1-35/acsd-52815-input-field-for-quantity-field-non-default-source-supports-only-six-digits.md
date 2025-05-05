---
title: 'ACSD-52815: 기본이 아닌 출처의 수량 필드에 대한 입력 필드는 최대 6자리까지만 지원합니다.'
description: ACSD-52815 패치를 적용하여 기본 재고가 아닌 출처의 수량 필드에 대한 입력 필드가 기본 재고의 경우 8과 달리 최대 6자리만 지원하는 Adobe Commerce 성능 문제를 해결합니다.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: 기본이 아닌 출처의 수량 필드에 대한 입력 필드는 최대 6자리까지만 지원합니다.

ACSD-52815 패치는 기본 재고의 8과 달리, 기본값이 아닌 출처의 수량 필드에 대한 입력 필드가 최대 6자리를 지원하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52815입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기본 출처가 아닌 출처의 수량 필드에 대한 입력 필드는 기본 재고의 경우 8과 달리 최대 6자리까지만 지원합니다.

<u>재현 단계</u>:

1. 새 주식과 소스를 만듭니다.
1. 새 소스 스톡이 123으로 설정된 제품을 만듭니다.
1. 판매 가능 수량(123)을 확인합니다.
1. 출처 수량을 12345678으로 갱신합니다.
1. 판매 가능 수량을 다시 확인합니다.

<u>예상 결과</u>:

판매 가능 수량이 정확한 양을 표시합니다.

<u>실제 결과</u>:

판매 가능 수량은 999999.9999입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
