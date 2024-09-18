---
title: '''ACSD-59514: 관리자의 Forms( [!DNL Page Builder] 브라우저 콘솔에서 오류 발생'')'
description: ACSD-59514 패치를 적용하여  [!DNL Page Builder] 이(가) 있는 관리자의 양식이 잠금을 해제하지 않고 5초 동안 "[!DNL Page Builder]" 오류를 발생시키는 Adobe Commerce 문제를 해결합니다." 을 클릭합니다. 양식을 제출한 후 브라우저 콘솔에서 변경 사항을 저장할 수 없습니다.
feature: Page Builder
role: Admin, Developer
source-git-commit: 19ecaa6b287d63bfae00c51911b53e1ed7ab5ed8
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-59514: 관리자의 Forms([!DNL Page Builder] 포함)에서 브라우저 콘솔에 오류가 발생합니다.

ACSD-59514 패치는 [!DNL Page Builder]을(를) 가진 관리자의 양식에서 *[!DNL Page Builder]이(가) 잠금을 해제하지 않고 5초 동안 렌더링하는 오류를 throw하는 문제를 해결합니다.양식을 제출한 후 브라우저 콘솔에서*&#x200B;을(를) 실행하므로 변경 내용을 저장할 수 없습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-59514입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Page Builder]이(가) 있는 관리자의 Forms에서 *[!DNL Page Builder]이(가) 잠금을 해제하지 않고 5초 동안 렌더링하는 동안 오류가 발생합니다.양식을 제출한 후 브라우저 콘솔에서*&#x200B;을(를) 실행하므로 변경 내용을 저장할 수 없습니다.

<u>필수 구성 요소</u>:

Adobe Commerce [!DNL Page Builder] 모듈이 설치되고 사용하도록 설정되었습니다.

<u>재현 단계</u>:

1. 관리자 패널을 열고 [!UICONTROL Content] 단추를 클릭합니다.
1. 블록을 선택하고 블록을 편집합니다.
1. 콘텐츠를 변경하고 [!UICONTROL Save]을(를) 클릭합니다.
1. 콘솔을 열고 오류 메시지를 확인합니다.

<u>예상 결과</u>:

블록이 정상적으로 저장되었습니다.

<u>실제 결과</u>:

로더가 회전을 멈추지 않고 블록이 저장되지 않습니다. 브라우저 콘솔에 다음 오류가 표시됩니다.
*[!DNL Page Builder]이(가) 잠금을 해제하지 않고 5초 동안 렌더링하고 있습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
