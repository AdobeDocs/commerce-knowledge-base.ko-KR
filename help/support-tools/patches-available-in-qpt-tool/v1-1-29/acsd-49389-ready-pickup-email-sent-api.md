---
title: 'ACSD-49389: 픽업 준비가 되지 않은 경우 API에서 보낸 픽업 이메일 준비'
description: ACSD-49389 패치를 적용하여 주문이 픽업 준비가 되지 않은 경우 API로 픽업 준비 이메일이 전송되는 Adobe Commerce 문제를 수정합니다.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: 픽업 준비가 되지 않은 경우 API에서 보낸 픽업 이메일 준비

ACSD-49389 패치는 주문이 픽업 준비가 되지 않은 경우 API에서 픽업 준비 이메일이 전송되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49389입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [QPT 랜딩 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)에서 호환성을 확인하십시오. 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문이 픽업 준비가 되지 않은 경우 API에서 픽업 준비 이메일이 전송됩니다.

<u>재현 단계</u>:

1. *[!UICONTROL In-Store Delivery]* 메서드를 사용하도록 설정합니다.
1. 픽업 위치가 활성화된 스톡 소스를 만듭니다.
1. 위에서 만든 소스로 기본 웹 사이트를 사용하여 새 스톡을 만듭니다.
1. 동일한 소스를 할당하는 제품을 만듭니다.
1. 재고 수량 = 1을 설정합니다.
1. 상점 첫 화면에서 *[!UICONTROL In-Store Delivery]* 메서드를 사용하여 4단계에서 만든 제품을 확인하십시오.
1. 주문에 대한 송장을 생성합니다.
1. 제품의 수량을 *0*(으)로 설정하여 재고가 없게 만듭니다.
1. 다음 API 요청 게시:

```
{
    "orderIds": [
        1
    ]
}
```

<u>예상 결과</u>:

픽업 준비가 된 이메일이 전송되지 않았습니다.

<u>실제 결과</u>:

API에서 *주문 준비가 되지 않았습니다*. 픽업 준비가 된 전자 메일이 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서의 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하세요.
