---
title: 'ACSD-48417: 일정 변경을 만든 후 SQL 오류 발생'
description: ACSD-48417 패치를 적용하여 제품에 대한 일정 변경을 작성하고 다른 제품을 저장한 후 SQL 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: 일정 변경을 만든 후 SQL 오류 발생

ACSD-48417 패치는 제품에 대한 일정 변경을 만들고 다른 제품을 저장한 후 SQL 오류가 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48417입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품에 대한 일정 변경을 생성하고 다른 제품을 저장한 후 SQL 오류가 나타납니다.

<u>재현 단계</u>:

1. Magento 2.4 설치 - EE + 샘플 데이터를 개발합니다.
1. 관리 패널 > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동합니다.
1. 모든 제품(예: Joust Duffle Bag [SKU: 24-MB01])을 편집합니다.
1. 새 업데이트 예약:
   * **[!UICONTROL Save as a New Update]** 선택
   * 업데이트 이름: &quot;업데이트 1&quot;
   * 시작 날짜: 현재 시간 +1분
   * 종료 날짜: 현재 시간 +1시간
   * 제품 이름을 다음으로 수정: &quot;Joust Duffle Bag 2&quot;
   * 제품을 저장합니다.
1. CLI로 이동한 다음 cron을 실행하고 일정이 적용될 때까지 기다립니다.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. 다시 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 구성 가능한 제품을 편집하십시오(예: Chaz Kangeroo Hoodie [SKU: MH01]).

   * 모든 변형을 비활성화합니다. 작업 열 > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**(으)로 이동합니다.
   * 구성 가능한 파일을 저장합니다.

<u>예상 결과</u>:

제품을 저장할 때 오류가 발생하지 않습니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
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
