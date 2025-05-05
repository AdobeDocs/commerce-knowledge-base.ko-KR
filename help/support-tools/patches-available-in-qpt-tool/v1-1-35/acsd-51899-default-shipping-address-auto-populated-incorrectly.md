---
title: 'ACSD-51899: 기본 배송 주소가 잘못 입력됨'
description: ACSD-51899 패치를 적용하여 기본 배송 주소가 잘못된 주소로 자동 채워지는 Adobe Commerce 문제를 해결합니다.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: 기본 배송 주소가 잘못 입력됨

ACSD-51899 패치는 기본 배송 주소가 잘못된 주소로 자동 채워지는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51899입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기본 배송 주소가 잘못된 주소로 자동 채워집니다.

<u>재현 단계</u>:

1. 배송 방법 아래의 **매장 픽업**&#x200B;을(를) 사용하도록 설정하십시오.
1. *스톡* 및 *소스*&#x200B;을 만듭니다.
1. 제품을 만들고 제품을 소스에 할당합니다.
1. 장바구니에 제품을 추가합니다.
1. 미니 장바구니에서 **체크아웃으로 진행**&#x200B;을 클릭합니다.
1. 테스트 전자 메일 주소를 입력하고 **스토어에서 선택**&#x200B;을 선택합니다.
1. **스토어 선택** 단추를 클릭하고 선택할 스토어 위치를 선택합니다.
1. **다음** 단추를 클릭합니다.
1. 스토어 로고를 클릭하여 **홈 페이지**(으)로 이동합니다.
1. **미니 장바구니**&#x200B;를 엽니다.
1. **장바구니 보기 및 편집**&#x200B;이라는 맨 아래 하이퍼링크를 클릭합니다.
1. **체크아웃 진행**&#x200B;을 클릭합니다.
1. 배송 페이지에서 배송 버튼을 클릭합니다.

<u>예상 결과</u>

배송 주소 필드는 *국가, 지역 및 우편 번호*&#x200B;를 제외하고 비어 있습니다.

<u>실제 결과</u>

기본 배송 주소는 페이지를 새로 고친 후 *매장 내 픽업* 주소로 자동 채워집니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
