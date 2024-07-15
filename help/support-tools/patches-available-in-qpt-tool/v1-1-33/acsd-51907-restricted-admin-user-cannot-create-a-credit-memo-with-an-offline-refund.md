---
title: "ACSD-51907: 제한된 관리자가 오프라인 환불에 대한 대변 메모를 만들 수 없음"
description: ACSD-51907 패치를 적용하여 제한된 관리 사용자가 오프라인 환급으로 대변 메모를 만들 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: 제한된 관리자가 오프라인 환불에 대한 대변 메모를 만들 수 없음

ACSD-51907 패치는 제한된 관리자가 오프라인 환불로 대변 메모를 만들 수 없는 성능 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51907입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제한된 관리자는 오프라인 환불로 대변 메모를 만들 수 없습니다.

<u>재현 단계</u>:

1. 기본 웹 사이트에 **customer**&#x200B;을(를) 만듭니다.
1. 관련 *스토어* 및 *스토어 보기*&#x200B;를 사용하여 **새 웹 사이트**&#x200B;를 만듭니다.
1. 기본 웹 사이트를 새 웹 사이트로 설정하고 캐시를 지웁니다.
1. 고객 구성 변경: **관리자** > **스토어** > **구성** > **고객** > **고객 구성** > **고객 계정 공유 = 전역**.
1. **관리자** > **시스템** > **권한**&#x200B;에서 역할 범위가 새로 만든 웹 사이트 *(판매 데이터에만 액세스)*(으)로 설정된 새 관리자 역할을 만듭니다.
1. 이 역할로 새 관리자 계정을 만듭니다.
1. 온라인 결제 방법 *(예: Auth.net 또는 PayPal)*&#x200B;을(를) 사용하여 새 주문을 만드십시오.
1. 제한된 관리자로 로그인합니다.
1. **판매** > **주문** > **페이지 보기**(으)로 이동합니다.
1. 송장을 생성합니다.
1. 송장 탭으로 이동합니다.
1. **청구서**&#x200B;를 클릭합니다.
1. **[!UICONTROL Credit Memo]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Refund to Store Credit]** 확인란을 선택하고 해당 확인란과 가까운 텍스트 필드를 *1* 값으로 설정합니다.
1. **[!UICONTROL Refund Offline]** 단추를 클릭합니다.

<u>예상 결과</u>:

대변 메모가 만들어지고 *$1*&#x200B;이(가) 스토어 크레딧으로 환불됩니다.

<u>실제 결과</u>:

*이 항목을 보려면 더 많은 권한이 필요합니다* 오류 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
