---
title: Adobe Commerce 지원 기술 자료
description: Commerce 스토어의 문제를 해결하고 유지 관리하는 데 필요한 모든 정보입니다.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 0%

---

# Adobe Commerce 지원 기술 자료

>[!NOTE]
>
>Adobe Commerce 지원 기술 자료 가이드는 곧 재구성되어 콘텐츠가 Adobe Experience League 내의 다른 위치로 이동됩니다. 당분간은 이 안내서의 콘텐츠를 계속 유지 관리하고 업데이트할 예정입니다.

![기술 자료 홈 페이지](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

이 기술 자료의 정보는 [Adobe Commerce 개발자 설명서](https://developer.adobe.com/commerce/docs), [Adobe Commerce 판매자 안내서](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) 및 기타 Adobe Commerce 발행물을 보완하는 것으로 디자인되었습니다. 문제 해결 및 모범 사례를 다루고, 발표를 호스팅하고, FAQ에 답변하고, 공식 설명서에서 (어떤 이유로든) 언급되지 않은 특정 시나리오를 강조합니다.

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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">보안 검색 도구에서 "서버가 2FA를 사용하는지 확인할 수 없음":</a>을 반환합니다. 오류를 해결하려면 <code>Magento_TwoFactorAuth</code> 모듈이 비활성화되었는지 확인하십시오. 일반적으로 검사를 통과하려면 이 확인란을 활성화해야 합니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632: 모든 주문 시도와 함께 저장된 주소:</a> ACSD-60632 패치는 주문이 성공적으로 생성되었는지 여부에 관계없이 각 주문 배치 시도와 함께 새 주소가 저장되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.51이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326: 고객 반환 상태에 대한 GraphQL 쿼리에서 오류가 발생합니다.</a> ACSD-60326 패치는 고객 반환 상태에 대한 GraphQL 쿼리에서 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.51이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925: GraphQL에서 미디어 갤러리의 항목을 위치별로 정렬합니다.</a> ACSD-59925 패치를 사용하면 미디어 갤러리의 항목이 위치별로 정렬되지 않아 잘못된 표시 순서가 발생하는 문제가 해결됩니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.52가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322: 공유 카탈로그에 할당되지 않은 제품이 XML 사이트 맵에 포함됨:</a> ACSD-61322 패치는 기본(일반) 그룹의 공유 카탈로그에 할당되지 않은 제품/범주가 여전히 XML 사이트 맵에 포함된 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.52가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590: 매일 보고서를 집계한 베스트셀러의 성능 향상:</a> ACSD-60590 패치를 사용하면 매일 보고서를 집계한 베스트셀러가 많은 양의 주문을 처리하는 데 상당한 시간이 걸리는 문제를 해결할 수 있습니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.52가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865: 장바구니 가격 규칙이 제품 수량이 부족하여 이전 규칙을 취소하지 못했습니다.</a> ACSD-59865 패치는 <em>고정 금액 할인</em>, <em>제품 가격 할인의 백분율</em> 및 <em>X 구매</em>에서 <em>할인 수량 단계</em> 값이 이전 규칙을 취소하지 않는 문제를 해결했습니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.52가 설치되어 있을 때 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">관리자의 주문을 필터링할 때 오류 발생:</a> 이 문서에서는 날짜별로 관리자의 주문을 필터링하려고 할 때 오류가 발생하는 Adobe Commerce 문제에 대한 패치를 제공하며, 메시지를 표시합니다. <em>무결성 제약 조건 위반: 1052 열 'created_at' where 절이 모호합니다</em>.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce: CSP(콘텐츠 보안 정책) 제한 모드의 체크아웃 페이지에 있는 인라인 JavaScript 문제:</a> 이 문서에서는 <strong>CSP 제한 모드</strong>를 사용할 수 있을 때 체크아웃 중에 Adobe Commerce 관리자 및 Adobe Commerce 2.4.7의 Google 태그 관리자를 통해 추가된 사용자 지정 JavaScript에서 발생하는 문제에 대한 자세한 설명과 솔루션을 제공합니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195: 장바구니 GraphQL 요청이 최종 페이지에서 항목을 반환하지 못했습니다.</a> ACSD-61195 패치는 장바구니 GraphQL 요청의 마지막 페이지에서 장바구니 항목이 반환되지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.51이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514: Page Builder가 있는 관리자의 Forms 브라우저 콘솔에서 throw 오류가 발생했습니다.</a> ACSD-59514 패치는 Page Builder가 있는 관리자의 양식에서 <em>양식을 제출한 후 브라우저 콘솔에서 잠금을 해제하지 않고 5초 동안 페이지 빌더가 렌더링하고 있었습니다</em> 변경 사항을 저장할 수 없는 문제를 해결했습니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538: <em>모든 스토어 보기</em>:</a>에서 제품이 비활성화된 경우 특성이 올바르게 표시되지 않습니다. ACSD-60538 패치는 제품이 <em>모든 스토어 보기</em>에서 비활성화되고 특정 스토어 보기 범위에서만 활성화된 경우 제품 특성이 GraphQL 응답에 올바르게 표시되지 않아 제품이 제대로 표시되지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.51이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352: 기본 저장소에 대한 반환 특성 레이블이 GraphQL API를 통해 반환됩니다.</a> ACSD-58352 패치는 요청 헤더에 기본이 아닌 저장소 보기가 지정된 경우 기본 저장소에 대한 반환 특성 레이블이 GraphQL API를 통해 반환되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">계정에서 <em>계정 전환</em> 드롭다운이 누락되었습니다.</a> 이 문서에서는 계정에서 <em>계정 전환</em> 드롭다운이 누락되어 판매자를 대신하여 티켓을 제출할 수 있는 액세스 권한이 상실된 Adobe Commerce 문제에 대한 솔루션을 제공합니다.
    </td>
    <td>새 문서</td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979: 스테이징 업데이트 삭제 후 제거된 제품 이미지:</a> ACSD-56979 패치는 스테이징 업데이트를 삭제한 후 제품 이미지가 제거되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.49가 설치된 경우에 사용할 수 있습니다.  
    </td>
    <td>새 문서</td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210: 저장소 보기 특정 범위 특성이 전역 값을 재정의합니다.</a> ACSD-48210 패치는 특정 저장소 보기 내에서 <em>웹 사이트 범위</em> 특성을 업데이트할 때 전역 범위의 특성 값을 재정의하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280: 2.4.4-pX 설치:</a>에서 ReflectionUnionType::getName() 오류 발생 ACSD-59280 패치는 정의되지 않은 메서드 <code>ReflectionUnionType::getName()</code> 호출이 2.4.4-pX 버전 설치 중에 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887: 고객 세션이 만료된 후 고객 장바구니를 지웁니다.</a> ACSD-54887 패치는 고객 세션이 만료된 후 <em>지속적인 장바구니</em>를 활성화하여 고객의 장바구니가 지워지는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303: HTML 축소가 활성화된 상태에서 해결된 관리자 주문 배치 문제:</a> HTML 축소가 활성화된 경우 ACSD-60303 패치가 관리자의 주문을 할 수 없는 문제를 수정합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045: <em>웹 사이트 루트</em>를 계층에서 선택 취소한 후 URL 다시 쓰기로 인해 무한 페이지 루프가 발생합니다.</a> ACSD-57045 패치는 <em>웹 사이트 루트</em>를 계층에서 선택 취소한 후 URL 다시 쓰기로 인해 무한 페이지 루프가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.49가 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446: GraphQL을 통해 하위 사용자 또는 팀이 있는 팀을 삭제하면 다음과 같은 비정보 오류 메시지가 표시됩니다.</a> GraphQL을 통해 하위 사용자 또는 팀이 있는 팀을 삭제하면 UI와 일치하지 않는 비정보 오류 메시지가 반환되는 Adobe Commerce 문제가 ACSD-58446 패치로 수정되었습니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.49가 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735: YouTube API 키를 잘못 구성하면 저장소 보기 수준에서 비디오를 추가할 때 오류가 발생합니다.</a> ACSD-58735 패치는 저장소 보기 수준에서 YouTube 비디오를 추가할 때 잘못된 YouTube API 키 구성으로 인해 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.49가 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086: 사용 약관이 활성화된 비기본 웹 사이트의 주문이 잘못 처리됨:</a> ACSD-57086 패치는 사용 약관이 활성화된 비기본 웹 사이트에서 주문된 주문이 올바르게 처리되지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.49가 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141: L2 Redis 캐시가 활성화된 경우 로그인한 고객에 대한 POST 요청에서 PHPSESID가 다시 생성됩니다.</a> L2 Redis 캐시가 활성화된 경우 로그인한 고객에 대한 POST 요청에서 PHPSESID가 다시 생성되는 문제를 ACSD-58141 패치에서 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790: Chrome의 모바일 보기에서 제품 세부 사항 페이지 이미지의 핀치-투-줌 기능을 수정합니다.</a> ACSD-58790 패치는 Chrome의 모바일 보기에서 이미지가 예상대로 확대되지 않는 Adobe Commerce 문제를 수정합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442: 너비가 768px인 장치가 모바일로 처리되어 메뉴와 헤더가 데스크톱이 아닌 모바일 보기에서 로드되는 문제를 해결합니다.</a> ACSD-58442 패치는 너비가 768px인 장치가 모바일로 처리되어 메뉴와 헤더가 데스크톱이 아닌 모바일 보기에서 로드되는 Adobe Commerce 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.50이 설치된 경우에 사용할 수 있습니다.
    </td>
    <td>새 문서 </td>
    <td>2024년 10월 17일</td>
  </tr>
</table>
