---
title: 'ACSD-50336: 제품 경고 이메일이 전송되지 않음'
description: ACSD-50336 패치를 적용하여 제품이 재입고되거나 가격이 변경될 때 제품 경고 이메일이 전송되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 0fc51603-e74d-4ce7-9e67-42826ffbfab2
feature: Communications, Personalization, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-50336: 제품 경고 이메일이 전송되지 않음

ACSD-50336 패치는 제품이 재입고되거나 가격이 변경될 때 제품 경고 이메일이 전송되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-50336입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 재입고되거나 가격이 변경될 때 제품 경고 이메일은 전송되지 않습니다.

<u>필수 구성 요소</u>:

제품이 재고에 다시 추가되는 경우에 대한 제품 경고를 설정합니다.

<u>재현 단계</u>:

1. 상점 첫 화면에서 고객으로 로그인합니다.
1. 재고가 없는 제품을 엽니다.
1. 제품이 *재입고*&#x200B;될 때 알림을 받으려면 구독하세요.
1. [!UICONTROL Admin]에서 제품을 _다시 입고_&#x200B;되도록 업데이트하십시오.

<u>예상 결과</u>:

*재입고 중*&#x200B;인 제품에 대한 이메일 알림이 고객에게 전송됩니다.

<u>실제 결과</u>:

고객이 *재입고* 중인 제품에 대한 이메일 알림을 받지 못했습니다. 다음 오류가 로그에 나타납니다.

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
