---
title: 'MDVA-42326: 고객이 세션 시간 제한 후 체크아웃 시 오류 발생'
description: MDVA-42326 패치는 영구적 장바구니가 활성화되더라도 세션 시간 제한 후 체크아웃 시 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42326입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: 세션 시간 제한 후 체크아웃 시 고객이 오류 발생

MDVA-42326 패치는 영구적 장바구니가 활성화되더라도 세션 시간 제한 후 체크아웃 시 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42326입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

지속 장바구니가 활성화된 경우에도 세션 시간 초과 후 체크아웃 시 오류가 발생합니다.

<u>필수 구성 요소</u>:

1. **구성** > **일반** > **웹** > **기본 쿠키 설정** > **쿠키 수명**(으)로 이동하여 **120**(으)로 설정합니다.
1. **구성** > **고객** > **고객 구성** > **온라인 고객 옵션**(으)로 이동하여 두 값을 모두 **2**(으)로 설정합니다.
1. **구성** > **고객** > **지속적인 장바구니**(으)로 이동하여 **사용**(으)로 설정합니다.
1. **Config** > **Sales** > **결제 방법**(으)로 이동하여 **수표/금전 주문**&#x200B;을 제외한 모든 결제 방법을 끕니다(활성화되어야 함).

<u>재현 단계</u>:

1. 고객으로 로그인하고 일부 제품을 장바구니에 추가합니다.
1. 장바구니를 확인하십시오.
1. 2분 동안 기다립니다(사전 조건으로 설정됨). 세션이 시간 초과되어야 합니다.
1. **체크아웃으로 이동**&#x200B;을 클릭하고 페이지를 새로 고치지 마십시오.
1. 게스트로 체크아웃하고 배송 주소를 입력한 다음 배송 방법을 선택하십시오.
1. **다음**&#x200B;을 클릭합니다.
1. **검토 및 결제** 페이지에서 **주문**&#x200B;을 클릭하세요. 하나의 결제 수단만 허용되므로 고객은 결제 방법을 선택하지 않고 주문을 할 수 있어야 한다.

<u>예상 결과</u>:

고객이 주문할 수 있어야 합니다.

<u>실제 결과</u>:

고객에게 다음 오류가 발생합니다. *주소 유효성 검사 실패: 전자 메일의 형식이 잘못되었습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
