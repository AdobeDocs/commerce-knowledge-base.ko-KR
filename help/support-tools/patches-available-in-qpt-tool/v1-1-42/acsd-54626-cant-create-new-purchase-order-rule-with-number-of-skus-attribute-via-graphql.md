---
title: 'ACSD-54626: GraphQL을 통해 NUMBER_OF_SKUS로 새 구매 주문 규칙을 만들 수 없음'
description: ACSD-54626 패치를 적용하여 고객이 GraphQL을 통해 'NUMBER_OF_SKUS' 속성으로 새 구매 주문 규칙('createPurchaseOrderApprovalRule')을 생성할 수 없는 Adobe Commerce 문제를 수정합니다.
feature: Attributes, B2B, GraphQL, Purchase Orders
role: Admin, Developer
exl-id: 807f06e3-6708-4860-bf46-df4404124f27
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54626: GraphQL을 통해 NUMBER_OF_SKUS로 새 구매 주문 규칙을 만들 수 없음

ACSD-54626 패치는 고객이 GraphQL을 통해 `NUMBER_OF_SKUS` 특성을 사용하여 새 구매 주문 규칙(`createPurchaseOrderApprovalRule`)을 만들 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-54626입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객이 GraphQL을 통해 `NUMBER_OF_SKUS` 특성을 사용하여 새 구매 주문 규칙(`createPurchaseOrderApprovalRule`)을 만들 수 없습니다.

<u>필수 구성 요소</u>:

Adobe Commerce B2B 모듈을 설치하고 활성화합니다.

<u>재현 단계</u>:

1. B2B 회사 및 구매 규칙을 활성화합니다.
1. 구매 규칙이 활성화된 회사를 만듭니다.
1. 다음 GraphQL 쿼리를 실행합니다.

   ```
   mutation CreatePurchaseRule {
       createPurchaseOrderApprovalRule(
           input: {
               name: "Test Rule"
               description: "description"
               applies_to: "MQ=="
               status: ENABLED
               approvers: "MQ=="
               condition: {
                   attribute: NUMBER_OF_SKUS
                   operator: MORE_THAN
                   quantity: 10
               }
           }
       ) {
           uid
           name
           __typename
       }
   }
   ```

<u>예상 결과</u>:

구매 규칙이 생성됩니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.

```
{
    "errors": [
        {
            "message": "Required data is missing from a rule condition.",
            "locations": [
                {
                    "line": 2,
                    "column": 3
                }
            ],
            "path": [
                "createPurchaseOrderApprovalRule"
            ],
            "extensions": {
                "category": "graphql-input"
            }
        }
    ],
    "data": {
        "createPurchaseOrderApprovalRule": null
    }
}
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
