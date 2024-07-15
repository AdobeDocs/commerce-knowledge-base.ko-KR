---
title: '특성 값에 쉼표가 포함된 경우 ACSD-48313: [!UICONTROL configurable_variations] 열이 구문 분석되지 않음'
description: ACSD-48313 패치를 적용하여 특성 값에 쉼표가 포함된 경우 [!UICONTROL configurable_variations] 열이 구문 분석되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 0ac3f8da-4da3-4308-bea4-98a5b6926b0d
feature: Attributes, Configuration
role: Admin
source-git-commit: 4cb43c4f16238253fc7fc75d9af9b921dfa74158
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313: 특성 값에 쉼표가 포함된 경우 **[!UICONTROL configurable_variations]** 열이 구문 분석되지 않음

ACSD-48313 패치는 특성 값에 쉼표가 포함되어 있으면 **[!UICONTROL configurable_variations]** 열이 구문 분석되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-48313입니다. 이 문제가 수정되는 버전은 아직 사용할 수 없습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품을 내보낸 후 **[!UICONTROL configurable_variations]** 특성의 서식 문제로 인해 결과 파일을 다시 가져올 수 없습니다. 이 문제는 쉼표를 포함하는 속성 옵션이 있을 때 발생합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**(으)로 이동하여 새 특성 _크기_&#x200B;를 만듭니다.
1. 저장소 소유자에 대한 카탈로그 입력 형식: **[!UICONTROL Dropdown]**.
1. 쉼표를 포함하는 옵션을 만듭니다. 예:
   * 10,2센티미터
   * 15,5센티미터
1. **[!UICONTROL Advanced Attribute Properties]** - 범위: _전역_.
1. 구성 만들기 기능을 사용하여 구성 가능한 새 제품을 만듭니다.
1. 위의 _Size_ 특성과 쉼표를 포함하는 두 옵션을 선택하십시오.
1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**(으)로 이동하여 새 제품 내보내기를 만듭니다(cron을 실행하여 CSV 파일 생성을 트리거하십시오).
1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**(으)로 이동한 다음 위에서 만든 것과 동일한 CSV 파일을 다시 가져오십시오.

<u>예상 결과</u>:

파일을 가져올 수 있어야 합니다.

<u>실제 결과</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
