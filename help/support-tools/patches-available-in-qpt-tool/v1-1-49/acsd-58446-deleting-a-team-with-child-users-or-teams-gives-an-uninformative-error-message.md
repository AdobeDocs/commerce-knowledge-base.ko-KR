---
title: 'ACSD-58446: GraphQL을 통해 하위 사용자 또는 팀이 있는 팀을 삭제하면 알 수 없는 오류 메시지가 표시됨'
description: ACSD-58446 패치를 적용하여 GraphQL을 통해 하위 사용자 또는 팀이 있는 팀을 삭제하면 UI와 일치하지 않는 정보 불가능한 오류 메시지가 반환되는 Adobe Commerce 문제를 해결합니다.
feature: Product, GraphQL, Company
role: Admin, Developer
source-git-commit: ab290f7c5b052aa220b3ef003febd9afc1cfdf00
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-58446: GraphQL을 통해 하위 사용자 또는 팀이 있는 팀을 삭제하면 알 수 없는 오류 메시지가 표시됩니다

ACSD-58446 패치는 Adobe Commerce에서 GraphQL을 통해 하위 사용자 또는 팀이 있는 팀을 삭제하면 UI와 일관되지 않은 비정보 오류 메시지가 반환되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58446입니다. 이 문제는 Adobe Commerce B2B 1.5.1에서 수정됩니다

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 및 Magento Open Source 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL을 통해 하위 사용자 또는 팀이 있는 팀을 삭제하면 UI와 일치하지 않는 비정보 오류 메시지가 반환됩니다.

## 전제 조건:

B2B 모듈을 설치했습니다.

<u>재현 단계</u>:

1. *[!UICONTROL Company]* 기능을 사용하도록 설정합니다.
1. 새 회사 계정을 만듭니다.
1. **[!UICONTROL Admin]**&#x200B;에 로그인하여 회사 계정을 활성화하십시오.
1. 이메일을 확인하고 새 회사 계정의 암호를 설정합니다.
1. 회사에 대한 새 팀을 만듭니다.
1. 프론트엔드에서 **[!UICONTROL company user]**(으)로 로그인하고 만든 팀에 대해 **[!UICONTROL new user]**&#x200B;을(를) 추가합니다.
1. **[!UICONTROL Admin]**&#x200B;에 로그인하고 회사 사용자를 사용하지 않도록 설정한 다음 *[!UICONTROL Customer Active]* = *아니요*&#x200B;를 설정합니다.
1. GraphQL을 통해 만든 팀을 삭제해야 합니다.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>예상 결과</u>:

UI와 일치하는 정보 제공용 오류 메시지가 반환됩니다.

<u>실제 결과</u>:

일반 내부 서버 오류 메시지가 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
