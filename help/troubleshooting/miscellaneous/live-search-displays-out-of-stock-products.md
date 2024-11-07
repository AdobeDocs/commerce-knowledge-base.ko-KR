---
title: '''[!DNL Live Search]''은(는) 관리자의 재고 상태 설정에 관계없이 품절 제품을 표시합니다.'''
description: 이 문서에서는 검색 팝오버가 일부 항목을 반환하는 동안 PLP(제품 목록 페이지)에 *선택* 오류와 일치하는 제품을 찾을 수 없습니다.*가 표시되는 알려진 문제에 대해 설명합니다.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search]은(는) 관리자의 재고 상태 설정에 관계없이 품절 제품을 표시합니다.

>[!IMPORTANT]
>
>이 문제는 [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html)에서 해결되었습니다. 최신 버전을 설치하려면 사용 안내서에서 [업데이트 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update)를 참조하세요.

이 문서에서는 검색 팝오버가 일부 항목을 반환하는 동안 PLP(제품 목록 페이지)에 *선택 항목과 일치하는 제품을 찾을 수 없습니다* 오류가 표시되는 알려진 문제에 대한 정보를 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 2.4.x

## 문제

[!DNL Live Search]은(는) Adobe Commerce 관리자의 재고 상태 설정에 관계없이 검색 결과를 표시합니다. **[!UICONTROL Display Out-of-Stock Products]**&#x200B;이(가) *아니요*(으)로 설정되어 있어도 제품이 표시됩니다. PLP 오류 *선택 항목과 일치하는 제품을 찾을 수 없습니다*.

<u>재현 단계</u>:

1. 카테고리를 만들고 제품을 추가합니다. (예: 범주 = _청바지_, 제품1 = _청바지_, 제품2 = _검은 청바지_)
1. 해당 범주의 모든 제품을 품절합니다.
1. **[!UICONTROL Display Out-of-Stock Products]**&#x200B;을(를) *아니요*(으)로 설정합니다.
1. 상점 앞의 검색 필드에 *Jeans*&#x200B;을(를) 입력하십시오.
1. 팝업에서 **[!UICONTROL View All]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

PLP에서 *선택 항목과 일치하는 제품을 찾을 수 없습니다* 메시지가 표시되고 검색 팝업에 제품이 표시되지 않습니다.

<u>실제 결과</u>:

PLP에서 *선택 항목과 일치하는 제품을 찾을 수 없습니다* 메시지가 표시되고 두 제품 모두 검색 팝업에 표시됩니다.

## 솔루션

현재 이 문제에 대한 해결 방법은 없습니다. [!DNL Live Search] 팀은 곧 제품을 올바르게 표시하도록 [!DNL Live Search]을(를) 구성할 수 있는 설정을 제공할 예정입니다.

## 관련 읽기

사용 안내서에서 [설치 [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)
