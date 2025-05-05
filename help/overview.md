---
title: Adobe Commerce 지원 기술 자료
description: Commerce 스토어의 문제를 해결하고 유지 관리하는 데 필요한 모든 정보입니다.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 6d22ea4725249df1528625672be405464b1411e8
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---

# Adobe Commerce 지원 기술 자료

>[!NOTE]
>
>Adobe Commerce 지원 기술 자료 가이드는 곧 재구성되어 콘텐츠가 Adobe Experience League 내의 다른 위치로 이동됩니다. 당분간은 이 안내서의 콘텐츠를 계속 유지 관리하고 업데이트할 예정입니다.

![기술 자료 홈 페이지](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

이 기술 자료의 정보는 [Adobe Commerce 개발자 설명서](https://developer.adobe.com/commerce/docs), [Adobe Commerce 판매자 안내서](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=ko) 및 기타 Adobe Commerce 발행물을 보완하는 것으로 디자인되었습니다. 문제 해결 및 모범 사례를 다루고, 발표를 호스팅하고, FAQ에 답변하고, 공식 설명서에서 (어떤 이유로든) 언급되지 않은 특정 시나리오를 강조합니다.

## 이 기술 자료에는 무엇이 있습니까?

| 범주 | 설명 |
| --- | --- |
| [지원 도구](/help/support-tools/overview.md) | Adobe Commerce에서 제공하는 다양한 지원 도구를 사용하여 전자 상거래 스토어 경험을 개선합니다. 당사는 개인화된 모범 사례, 진단 및 모니터링 도구, 귀하의 사이트에 대한 가장 관련성이 높은 정보를 제공합니다. |
| [공지](/help/announcements/overview.md) | Adobe Commerce 팀으로부터 중요한 업데이트를 받으십시오. |
| [문제 해결](/help/troubleshooting/overview.md) | Adobe Commerce 지원 팀으로부터 셀프서비스 솔루션 및 패치를 받으십시오. |
| [도움말 센터 사용 안내서](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | 지원 티켓을 관리하고, 공유 액세스 권한을 부여하고, 기술 자료를 효과적으로 탐색하는 방법에 대해 알아봅니다. |
| [방법](/help/how-to/overview.md) | Adobe Commerce 지원 팀에서 명확한 단계별 지침을 받아 보십시오. |
| [FAQ](/help/faq/overview.md) | Adobe Commerce 정책, 전략 및 Adobe Commerce 기능에 대한 세부 사항에 대해 자주 묻는 질문을 찾아보십시오. |

## 새로운 기능

<table style="width:100%">
  <tr>
    <th style="width:70%">설명</th>
    <th style="width:15%">유형</th>
    <th style="width:15%">날짜</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25301">Adobe Commerce에서 PHP 8.2에서 8.3으로 업그레이드할 때 [!DNL New Relic] 에이전트 문제 해결:</a> PHP를 버전 8.2에서 8.3으로 업그레이드하면 [!DNL New Relic] 에이전트가 Adobe Commerce 환경에서 작동하지 않을 수 있습니다. 이 문제는 스테이징 및 프로덕션 환경에서 발견되었습니다. 이 문서에서 이 문제를 해결하고 해결하는 절차를 찾을 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25321">[!DNL Security Scan Tool]은(는) 패치가 이미 적용된 경우에도 "APSByy-xx 보안 업데이트를 사용할 수 있음"을 반환합니다.</a> [!DNL Security Scan Tool]은(는) 사용자가 이미 패치를 적용한 경우에도 Adobe Commerce 및 Magento Open Source에서 사용할 수 있는 APSByy-xx 보안 업데이트를 보고합니다. 이 알림은 무시해도 됩니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61845-error-occurs-for-requests-with-text-html-accept-header">ACSD-61845: text/html accept 헤더가 있는 요청에 오류가 발생했습니다.</a> ACSD-61845 패치는 텍스트/html accept 헤더만 있는 HTTP 요청에서 응답 처리 시 미디어 유형 불일치로 인해 500 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.54가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61200-fixes-discount-tax-compensation-in-sales-total-calculations">ACSD-61200: 판매 총 계산에서 잘못된 할인 세금 보상:</a> ACSD-61200 패치는 할인 세금 보상 금액 및 운송 할인 세금 보상 금액이 총 금액 및 총 금액 실제 계산에서 누락되어 판매 주문 데이터와 쿠폰 보고서 데이터가 일치하지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.54가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61199-cms-page-hierarchy-tab-doesnt-display-proper-tree-structure">ACSD-61199: CMS 페이지의 [!UICONTROL Hierarchy] 탭에 적절한 트리 구조가 표시되지 않습니다.</a> 기존 계층 구조로 CMS 페이지를 편집할 때 ACSD-61199 패치가 CMS 페이지의 [!UICONTROL Hierarchy] 탭에 적절한 트리 구조가 표시되지 않는 문제를 해결했습니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.54가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60804-editing-customer-linked-to-deleted-company-causes-error">ACSD-60804: 삭제된 회사와 연결된 고객을 편집하면 다음 오류가 발생합니다.</a> ACSD-60804 패치는 삭제된 회사와 연결된 고객을 편집하면 <em>null에 멤버 함수 getSuperUserId()를 호출하는 </em> 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.53이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61522-email-in-name-fields-sends-invalid-order-confirmations">ACSD-61522: [!UICONTROL First] 및 [!UICONTROL Last Name] 필드의 전자 메일 주소에서 잘못된 주문 확인을 보냅니다.</a> ACSD-61522 패치는 게스트 고객의 [!UICONTROL First Name] 및 [!UICONTROL Last Name] 필드에 전자 메일 주소를 입력할 수 있어 잘못된 주문 확인 전자 메일이 전송되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.54가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-62485-async-operations-all-consumer-stops-working-when-company-is-created">ACSD-62485: <code>async.operations.all</code> 소비자가 회사를 만들 때 작동을 중지함:</a> ACSD-62485 패치는 B2B 회사가 만들어질 때 <code>async.operations.all</code> 소비자가 작동을 중지하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.54가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60684-graphql-product-sorting-by-multiple-fields-does-not-work-as-expected">ACSD-60684: 여러 필드를 기준으로 한 GraphQL 제품 정렬이 예상대로 작동하지 않습니다.</a> ACSD-60684 패치는 정렬이 변수로 전달될 때 여러 필드를 기준으로 한 GraphQL 제품 정렬이 작동하지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.52가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    61553 <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61553-cart-price-rule-discounts-are-incorrectly-calculated-when-multiple-discounts-with-different-priorities-are-applied">우선 순위가 다른 여러 할인을 적용할 때 [!UICONTROL Cart Price Rule]이(가) 잘못 계산됨:</a> ACSD-61553 패치는 우선 순위가 다른 여러 할인을 적용할 때 [!UICONTROL Cart Price Rule]이(가) 잘못 계산되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.53이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58383-duplicate-credit-memos-from-simultaneous-refund-requests-via-rest-api">ACSD-58383 Adobe Commerce 패치: REST API를 통해 동시 환불 요청에서 중복된 대변 메모:</a> ACSD-58383 패치는 동시에 실행되는 두 개의 동일한 요청으로 REST API를 통해 환불을 발행하면 중복 대변 메모가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.55가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58471-dynamic-content-fails-load-product-detail-page">ACSD-58471: 연결된 카탈로그 가격 규칙이 예약된 경우 동적 콘텐츠가 제품 세부 정보 페이지에서 로드되지 않습니다.</a> 연결된 카탈로그 가격 규칙이 예약된 경우 ACSD-58471 패치가 제품 세부 정보 페이지에서 동적 콘텐츠가 로드되지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.55가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58735-restricted-admin-cant-view-abandoned-shopping-carts">ACSD-58735: 제한된 관리자는 연결된 웹 사이트의 고객 계정에서 포기한 장바구니를 볼 수 없습니다.</a> ACSD-58735 패치는 제한된 역할을 가진 관리자가 <strong>[!UICONTROL Commerce Admin]</strong> &gt; <strong>[!UICONTROL Reports]</strong> &gt; <strong>[!UICONTROL Abandoned Carts]</strong> &gt; <strong>[!UICONTROL Select Cart]</strong> &gt; <strong>[!UICONTROL Shopping Cart]</strong> 탭에서 포기한 고객의 장바구니를 볼 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.55가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 12월 5일</td>
  </tr>
</table>
