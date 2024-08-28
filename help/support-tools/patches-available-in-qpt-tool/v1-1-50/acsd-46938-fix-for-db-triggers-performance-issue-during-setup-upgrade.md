---
title: '''ACSD-46938: ''setup:upgrade'' 중 DB 트리거에 성능 문제 발생'''
description: ACSD-46938 패치를 적용하여 'setup:upgrade' 명령이 인덱서 모드를 일정에서 저장으로 변경하여 성능 저하를 초래하는 Adobe Commerce 문제를 해결합니다.
feature: Upgrade
role: Admin, Developer
source-git-commit: cbd16ac7c6d6d7a4e3786880409475a10964c070
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46938: `setup:upgrade` 동안 DB 트리거에 성능 문제가 발생했습니다.

ACSD-46938 패치는 `setup:upgrade` 명령이 인덱서 모드를 일정에서 저장으로 변경하여 성능이 크게 저하되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46938입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`setup:upgrade`에서 DB 트리거 재생성 중 성능 저하.

<u>재현 단계</u>:

1. 많은 제품 및 범주로 구성된 큰 카탈로그를 만듭니다.
1. [!UICONTROL Admin]에 로그인합니다.
1. 모든 인덱서를 [!UICONTROL Update By Schedule] 모드로 설정합니다.
1. 제품을 엽니다.
1. 업데이트. 예를 들어 새 카테고리를 할당합니다.
1. [!UICONTROL Save]을(를) 클릭합니다.
1. `bin/magento setup:upgrade` 및 `bin/magento cron:run` 명령을 동시에 실행합니다.

<u>예상 결과</u>:

`bin/magento cron:run` 명령이 동시에 실행되면 `bin/magento setup:upgrade` 명령의 실행 시간이 크게 늘어납니다.

<u>실제 결과</u>:

명령 실행 시간은 늘어나지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
