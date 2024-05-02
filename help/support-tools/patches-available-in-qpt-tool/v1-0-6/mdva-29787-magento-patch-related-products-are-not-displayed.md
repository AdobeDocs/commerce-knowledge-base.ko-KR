---
title: 'MDVA-29787: 관련 제품이 표시되지 않음'
description: MDVA-29787 패치는 Adobe Commerce 스토어 프론트엔드에 **관련 제품**이 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-29787입니다.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787: 관련 제품이 표시되지 않음

MDVA-29787 패치는 다음과 같은 문제를 해결합니다. **관련 제품** 은 Adobe Commerce 스토어 프론트엔드에 표시되지 않습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치되었습니다. 패치 ID는 MDVA-29787입니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.3.

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.0.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

에 대한 대상 규칙 **관련 제품** 은(는) 일 때 작동하지 않습니다.*다음 중 하나*&quot; 상태가 다음에 사용됨 **표시할 제품** Commerce 관리자

>[!NOTE]
>
>참고: 이 패치는 기존 대상 규칙을 수정하지 않습니다. 기존 대상 규칙을 다시 만들어야 합니다.

<u>재현 단계</u>:

1. 만들기 **새 속성** (예: Test\_Attr).
   * 설정 **저장소 소유자에 대한 카탈로그 입력 유형** = *텍스트.*
   * 위치 **Storefront 속성**, 설정됨 **프로모션 규칙 조건에 사용** = *예*.
1. 만들기 **새 속성 집합** (예: Test\_Set).
1. 추가 **새 속성** (으)로 **새 속성 집합** (예: &quot;Test\_Set&quot; 속성 세트에 &quot;Test\_Attr&quot; 속성을 추가합니다.)
1. 세 가지 제품을 만듭니다. 예제의 경우 다음과 같이 설정됩니다.
   * Product1, Test\_Attr = MAGT2NA\_Test3
   * Product2, Test\_Attr = 24-MB02
   * Product3, Test\_Attr = 701644329389M
1. 대상 만들기 **규칙** (**마케팅**   > **관련 제품 규칙** 을(를) 클릭하고 **규칙 추가** 단추.) (설정 포함)
   * **적용 대상** = *관련 제품*
   * **일치하는 제품**
   * 만든 새 속성 설정 **위치:** **위의 1단계** Product1의 속성(예: Test\_Attr = MAGT2NA\_Test3).
   * **표시할 제품** = 다른 두 제품의 속성(예: 24-MB02 및 701644329389M 속성).
1. 저장 **규칙**.
1. 필요한 경우 색인 재지정을 실행합니다.
1. 캐시를 지웁니다.
1. 프론트엔드에서 Product1을 엽니다.

<u>예상 결과</u>:

관련 제품이 있습니다.

<u>실제 결과</u>:

관련 제품이 누락되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
