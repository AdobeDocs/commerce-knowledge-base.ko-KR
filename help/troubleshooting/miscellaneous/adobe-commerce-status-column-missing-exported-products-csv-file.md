---
title: Adobe Commerce 상태 열에 내보낸 제품 CSV 파일이 없음
description: 이 문서에서는 내보낸 제품이 포함된 CSV 파일에서 상태 열을 찾을 수 없는 문제에 대한 해결 방법을 제공합니다.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce 상태 열에 내보낸 제품 CSV 파일이 없음

이 문서에서는 내보낸 제품이 포함된 CSV 파일에서 상태 열(예: 제품의 활성화 또는 비활성화 여부 표시)을 찾을 수 없는 경우의 문제에 대한 해결 방법을 제공합니다. 제품 상태는 [!UICONTROL product_online] 열로 표시됩니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 모든 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 문제

내보낸 제품이 포함된 CSV 파일에서 [!UICONTROL status] 열을 찾을 수 없습니다. 따라서 예를 들어 모든 SKU의 CSV를 상태와 함께 내보내지만 테이블에 [!UICONTROL status] 열이 없는 것 같습니다.

<u>재현 단계:</u>

1. Adobe Commerce 관리에서 **[!UICONTROL System]**&#x200B;을(를) 선택하고 **[!UICONTROL Data Transfer]**&#x200B;에서 **[!UICONTROL Export]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Export Settings]** 섹션에서 **[!UICONTROL Entity Type]** 드롭다운 **[!UICONTROL Products]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Attribute Code]**&#x200B;에 나열된 **[!UICONTROL status]**&#x200B;을(를) 검색합니다. 사용 가능한 특성 목록(**[!UICONTROL Enable Product]**)에 해당 특성 코드가 표시됩니다.
1. **[!UICONTROL Export]**&#x200B;을(를) 클릭합니다.

<u>예상 결과:</u>

방금 내보낸 CSV 파일에 [!UICONTROL status](으)로 레이블이 지정된 열이 있습니다.

<u>실제 결과:</u>

내보낸 csv 파일에 [!UICONTROL status] 레이블이 지정된 열이 없습니다.

## 원인

제품의 상태 특성 이름이 CSV 파일에서 변경되었습니다. 이제 [!UICONTROL product_online] 열입니다.

## 솔루션

1. **[!UICONTROL System]**&#x200B;을(를) 선택하고 **[!UICONTROL Data Transfer]**&#x200B;에서 **[!UICONTROL Import]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Download Sample File]**&#x200B;을(를) 클릭합니다.
1. CSV 파일에서 [!UICONTROL product_online] 열이 표시됩니다.

## 관련 읽기

* 사용 안내서에서 [CSV 파일로 작업](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-csv).
* 사용 안내서의 [제품 내보내기 특성 참조](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-attributes-product).
