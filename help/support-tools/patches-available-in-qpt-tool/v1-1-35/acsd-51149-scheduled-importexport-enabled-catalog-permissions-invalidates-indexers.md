---
title: 'ACSD-51149: [!UICONTROL Catalog Permissions]이(가) 활성화된 예약된 [!UICONTROL ImportExport]이(가) 인덱서를 무효화합니다.'
description: ACSD-51149 패치를 적용하여 [!UICONTROL Catalog Permissions]이(가) 활성화된 예약된 [!UICONTROL ImportExport]이(가) 인덱서를 무효화하는 Adobe Commerce 성능 문제를 해결합니다.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: [!UICONTROL Catalog Permissions]이(가) 활성화된 예약된 [!UICONTROL ImportExport]이(가) 인덱서를 무효화합니다.

ACSD-51149 패치는 [!UICONTROL Catalog Permissions]이(가) 활성화된 예약된 [!UICONTROL ImportExport]이(가) 인덱서를 무효화하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51149입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Catalog Permissions]이(가) 활성화된 예약된 [!UICONTROL ImportExport]은(는) 인덱서를 무효화합니다.

<u>재현 단계</u>:

1. *[!UICONTROL Catalog Permissions]* 사용
1. 모든 인덱서를 *[!UICONTROL Update by Schedule]*(으)로 설정합니다.
1. 간단한 제품을 만듭니다.
1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**&#x200B;을(를) 통해 이 제품을 내보냅니다.
1. 내보낸 CSV를 다운로드하여 `<AC root folder>/var/import`에 넣습니다.
1. 다운로드한 CSV로 예약된 제품 가져오기를 만듭니다.
1. 전체 색인 재지정을 실행합니다.
1. 인덱서의 상태를 확인합니다. 모든 인덱서는 *[!UICONTROL Ready]* 상태여야 합니다.
1. 그리드에서 생성된 예약된 가져오기를 실행합니다.
1. 인덱서의 상태를 다시 확인하십시오.

<u>예상 결과</u>:

모든 인덱서가 *[!UICONTROL Ready]* 상태입니다.

<u>실제 결과</u>:

일부 인덱서가 *[!UICONTROL Reindex Required]* 상태입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
