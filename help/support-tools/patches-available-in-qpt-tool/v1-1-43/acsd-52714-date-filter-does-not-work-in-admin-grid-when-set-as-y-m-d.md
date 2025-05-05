---
title: 'ACSD-52714: y-m-d로 설정된 경우 날짜 필터가 관리 그리드에서 작동하지 않음'
description: ACSD-52714 패치를 적용하여 날짜 형식이 y-m-d로 설정된 경우 날짜 필터가 관리 그리드에서 작동하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Attributes
role: Admin, Developer
exl-id: b292ab2c-e12d-40df-a9ad-19f25fbde5a0
source-git-commit: 513cb47c054dbb907810bbdc3d20d2aca9d5e42b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-52714: y-m-d로 설정하면 날짜 필터가 관리 그리드에서 작동하지 않습니다

ACSD-52714 패치는 날짜 형식이 y-m-d로 설정된 경우 관리 그리드에서 날짜 필터가 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52714입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

날짜 형식이 y-m-d로 설정된 경우 날짜 필터가 관리 그리드에서 작동하지 않습니다.

<u>재현 단계</u>:

1. 깨끗한 Adobe Commerce을 설치합니다.
1. 편집
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
파일 및 추가
   `<dateFormat>Y-MM-dd</dateFormat>`
끝
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
태그 아래
   `<dataType>date</dataType>`

1. `bin/magento c:f` 캐시를 플러시합니다.
1. 관리자에 로그인하고 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;에서 새 고객을 만듭니다.

   * 시작: 현재 날짜에서 1일을 뺀 날짜
   * 종료: 현재 날짜

1. **[!UICONTROL Apply Filters]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

그리드의 날짜 필터는 로케일 설정에 관계없이 제대로 작동합니다.

<u>실제 결과</u>:

다음 메시지가 나타납니다. *레코드를 찾을 수 없습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
