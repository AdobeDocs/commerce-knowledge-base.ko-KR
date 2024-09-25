---
title: 관리자에서 주문을 필터링할 때 오류 발생
description: 이 문서에서는 "무결성 제한 위반 1052 열 'created_at' where 절이 모호함" 메시지를 표시하는 오류가있는 Adobe Commerce 문제에 대한 패치를 제공합니다.
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 관리자에서 주문을 필터링할 때 오류 발생

이 문서에서는 날짜별로 관리자의 주문을 필터링하려고 할 때 오류가 발생하는 Adobe Commerce 문제에 대한 패치를 제공합니다. 메시지를 표시합니다. *무결성 제약 조건 위반: 1052 열 &#39;created_at&#39; where 절 모호함*.

## 영향을 받는 버전

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7

## 문제

관리자의 주문을 날짜별로 필터링하면 오류가 반환됩니다.

exception.log는 다음을 표시합니다.

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>재현 단계:</u>

1. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동합니다.
   * 격자에서 **[!UICONTROL Purchase Date Ascending]** 순서 설정 또는
   * 필터에서 **[!UICONTROL Purchase Date Filter]**&#x200B;을(를) 설정합니다.

1. 오류가 나타납니다. *기본 보기를 처리하는 동안 문제가 발생하여 필터를 원래 상태로 복원했습니다.*

## 원인

[!DNL PayPal Braintree] 모듈에 문제가 있습니다.

## 솔루션

이 문제를 해결하려면 이 문서에 첨부된 패치를 적용합니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

이 패치는 영향을 받는 모든 버전 및 버전과 호환됩니다.

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.
