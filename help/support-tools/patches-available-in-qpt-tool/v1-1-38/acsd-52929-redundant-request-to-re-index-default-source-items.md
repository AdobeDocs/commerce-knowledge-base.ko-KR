---
title: 'ACSD-52929: 기본 소스 항목을 다시 색인화하기 위한 중복 요청'
description: ACSD-52929 패치를 적용하여 인벤토리 인덱서가 비동기 모드로 구성된 경우 기본 소스 항목을 다시 인덱싱하라는 중복 요청이 있는 Adobe Commerce 문제를 해결합니다.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929: 기본 소스 항목을 다시 색인화하기 위한 중복 요청

ACSD-52929 패치는 인벤토리 인덱서가 비동기 모드로 구성된 경우 기본 소스 항목을 다시 인덱싱하기 위한 요청이 중복되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.38이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52929입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

인벤토리 인덱서가 비동기 모드로 구성된 경우 기본 소스 항목을 다시 인덱싱하는 요청에 대한 중복이 있습니다.

<u>재현 단계</u>:

1. [!DNL RabbitMQ] 구성.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]**(으)로 이동하여 비동기 리인덱스 전략을 활성화하고 **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**&#x200B;을(를) 설정합니다.
1. 사용자 지정 인벤토리 소스를 만듭니다.
1. [!DNL RabbitMQ] 대시보드에 로그인하고 큐 탭으로 이동합니다.
1. `inventory.indexer.sourceItem` 큐를 확인하고 메시지가 없는지 확인하십시오.
1. 백엔드에서 간단한 제품을 열고 *[!UICONTROL stock only]*&#x200B;을(를) 사용자 지정 소스에 추가하고 제품을 저장합니다.
1. [!DNL RabbitMQ] 대시보드에 `inventory.indexer.sourceItem` 큐를 로드한 다음 메시지를 확인하십시오.

<u>예상 결과</u>:

사용자 지정 소스에 대한 대기열에는 메시지가 하나만 있습니다.

<u>실제 결과</u>:

대기열에는 기본 소스용 메시지와 사용자 정의 소스용 메시지, 이렇게 두 개의 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
