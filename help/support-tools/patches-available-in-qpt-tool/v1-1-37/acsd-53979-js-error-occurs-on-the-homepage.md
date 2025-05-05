---
title: 'ACSD-53979: 홈 페이지에서 JS 오류 발생'
description: 시작 메시지에 작은 따옴표가 포함된 경우 ACSD-53979 패치를 적용하여 홈 페이지에서 JavaScript 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Page Content
role: Admin, Developer
exl-id: 4e5afc5c-322f-4681-b2aa-01d93be74d4a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-53979: 홈 페이지에서 JavaScript 오류 발생

ACSD-53979 패치는 시작 메시지에 작은 따옴표가 포함된 경우 홈 페이지에서 JavaScript 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-53979입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

시작 메시지에 작은 따옴표가 포함된 경우 홈 페이지에서 JavaScript 오류가 발생합니다.

<u>재현 단계</u>:

1. 기본 환영 메시지를 [!DNL French] 언어로 `en_US.csv` 파일에 설정하거나 다음과 같이 인용 문자를 넣으십시오.
   `app/code/Magento/Theme/i18n/en_US.csv`

   ```CSV
       "Default welcome msg!","Message d'accueil par défaut"
   ```

1. 프론트엔드로 가세요

<u>예상 결과</u>:

프론트엔드는 JavaScript 오류 없이 로드됩니다.

<u>실제 결과</u>:

JavaScript 오류가 발생합니다.

```JS
    Uncaught SyntaxError: Unable to process binding "ifnot: function(){return customer().fullname }"
    Message: Unable to parse bindings.
    Bindings value: text: 'Message d'accueil par défaut'
    Message: Unexpected identifier 'accueil'
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
