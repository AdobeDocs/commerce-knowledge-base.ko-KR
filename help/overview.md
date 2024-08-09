---
title: Adobe Commerce 지원 기술 자료
description: Commerce 스토어의 문제를 해결하고 유지 관리하는 데 필요한 모든 정보입니다.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: cfbe281941fbdc3e6fe7ee36385dc6732b46da26
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 0%

---

# Adobe Commerce 지원 기술 자료

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

>[!NOTE]
>
>새 티켓을 제출하려면 [Adobe Commerce 도움말 센터](https://support.magento.com/)에 로그인하고 [지원 티켓 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)에 설명된 단계를 따르십시오.
>
>티켓을 제출하는 옵션이 표시되지 않으면 [도움말 센터 사용 안내서](/help/help-center-guide/help-center/magento-help-center-user-guide.md)의 *[표시되지 않은 티켓 링크 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* 섹션을 참조하십시오.

## 새로운 기능

<table style="width:100%">
  <tr>
    <th style="width:70%">설명</th>
    <th style="width:15%">유형</th>
    <th style="width:15%">날짜</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment"><code>Magento-cloud</code> CLI에 활성 환경이 표시되지 않습니다.</a> 활성 환경이 여러 개 있으며 Magento 클라우드 CLI(명령줄 도구) 명령을 실행하여 환경과 상호 작용하려고 합니다. 그러나 원하는 환경을 선택하라는 메시지가 이 환경을 나열하지 않습니다.
    </td>
    <td>새 문서</td>
    <td>2024년 7월 30일</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches">보안 패치를 가져오고 적용하는 방법:</a> 이 문서에서는 릴리스된 보안 패치를 가져오고 적용하는 방법에 대한 지침을 제공하지만, 지침을 사용할 수 없습니다.  
    </td>
    <td>새 문서</td>
    <td>2024년 7월 30일</td>
  </tr>

<tr>
    <td>
    검색 엔진이 Opensearch로 설정된 경우 <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch">Elasticsearch7로 폴백:</a> 이 문서에서는 검색 엔진이 Adobe Commerce에서 OpenSearch로 설정된 경우 Elasticsearch7로 폴백 오류가 발생하는 문제에 대한 해결 방법을 제공합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error">배포 실패: 'cache' 네임스페이스 오류에 정의된 명령이 없습니다.</a> 이 문서에서는 배포가 실패하고 로그에 표시된 오류 중 하나가 <em>"cache" 네임스페이스에 정의된 명령이 없습니다</em>. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response">ACSD-55566: <code>mergeCart</code> 돌연변이가 GraphQL 응답의 내부 서버 오류로 인해 실패합니다.</a> ACSD-55566 패치는 GraphQL 응답의 내부 서버 오류로 인해 <code>mergeCart</code> 돌연변이가 실패하는 문제를 수정합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다.  
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront">ACSD-56546: 구성 가능한 번들 제품이 상점 앞에 품절로 표시됨:</a> ACSD-56546 패치는 구성 가능한 번들 제품이 상점 앞에 품절로 표시되는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다.  
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information">ACSD-57565: 주문 대시보드에 잘못된 주문 정보가 표시됨:</a> ACSD-57565 패치는 기간이 업데이트될 때까지 주문 대시보드에 잘못된 주문 정보가 표시되는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql">ACSD-57394: GraphQL에서 여러 정렬 특성을 기준으로 한 잘못된 제품 정렬:</a> ACSD-57394 패치는 GraphQL에서 여러 정렬 특성을 사용할 때 제품이 잘못 정렬되는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations">ACSD-57854: GraphQL 응답에 범주 집계에 나열할 수 없는 비활성화된 범주가 포함되어 있습니다.</a> ACSD-57854 패치는 GraphQL 응답에 범주 집계에 나열할 수 없는 비활성화된 범주가 포함되어 있는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing">ACSD-57074: <code>attribute_code</code> 특성에 <code>price_*</code> 접두사가 있는 Yes/No 사용자 지정 특성이 인덱싱에서 작동하지 않습니다.</a> ACSD-57074 패치는 <code>attribute_code</code> 특성에 <code>price_*</code> 접두사가 있는 <em>Yes/No</em> 사용자 지정 특성이 인덱싱에서 작동하지 않는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons">ACSD-55241: 사용된 특성과 사용된 시간 특성이 생성된 쿠폰에 대해 잘못된 값을 표시함:</a> ACSD-55241 패치는 사용된 특성과 사용된 시간 특성이 생성된 쿠폰에 대해 잘못된 값을 표시하는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products">ACSD-56760: 관리자 사용자가 특정 웹 사이트로 제한되어 새 제품을 정렬 또는 추가할 수 없습니다.</a> ACSD-56760 패치는 특정 웹 사이트로 제한되어 있고 웹 스토어에 자체 루트 범주가 있는 경우 범주 내에서 새 제품을 정렬 또는 추가할 수 없는 관리자 사용자의 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address">ACSD-56635: 계정 공유를 Global로 설정하면 가져온 고객이 동일한 이메일 주소로 복제됩니다.</a> 가져오기를 Global로 설정하면 가져온 고객이 동일한 이메일 주소로 복제되는 문제가 ACSD-56635 패치로 해결됩니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked">ACSD-57315: 가져오기 단추를 클릭할 때마다 PayPal Payflow Pro에서 새 트랜잭션이 만들어집니다.</a> ACSD-57315 패치는 관리자의 트랜잭션 보기 화면에서 가져오기 단추를 클릭할 때마다 PayPal Payflow Pro에서 새 트랜잭션이 만들어지는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger">ACSD-56741: 사용자 지정 MySQL 트리거로 데이터베이스 설치 오류 문제 해결:</a> ACSD-56741 패치는 색인 지정 및 MView와 관련 없는 데이터베이스의 사용자 지정 MySQL 트리거로 인해 <code>setup:upgrade</code> 동안 <em>null 형식의 값에 대한 배열 오프셋에 액세스하려고 시도</em>하는 오류 메시지가 표시되는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear">ACSD-58008: 종료 날짜를 공백으로 편집하면 일정 업데이트가 사라집니다.</a> ACSD-58008 패치는 종료 날짜를 공백으로 편집하면 일정 업데이트가 사라지는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies">ACSD-57337: 액세스 제한이 있는 관리자가 회사 그리드의 모든 회사를 볼 수 있음:</a> ACSD-57337 패치는 특정 웹 사이트에 대한 액세스 제한이 있는 관리자가 회사 그리드의 모든 웹 사이트에서 회사를 볼 수 있는 문제를 해결합니다. 이 패치는 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48이 설치된 경우에 사용할 수 있습니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth">배포가 <code>env:COMPOSER_AUTH</code> 또는 <code>auth.json</code>에서 올바른 액세스 키를 사용하여 실패합니다.</a> 이 문서에서는 배포 로그에 있는 것과 같은 오류로 배포가 실패할 경우 이 문제에 대한 해결 방법을 제공합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests">GraphQL WAF 요청을 위해 WAF을 우회하는 방법:</a> 이 문서에서는 Fastly WAF이 GraphQL 요청을 차단할 때 GraphQL 요청을 우회하는 방법에 대해 설명합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full">내보내기 저장소가 거의 가득 찼음을 알리는 전자 메일:</a> 이 문서에서는 내보내기 저장소가 거의 가득 찼음을 알리는 전자 메일을 받는 문제에 대한 해결 방법을 제공합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud">클라우드에서 Adobe Commerce용 MariaDB 10.4에서 10.5로 업그레이드:</a> 이 문서에서는 클라우드 인프라에서 Adobe Commerce을 계속 사용하기 위해 MariaDB 10.4에서 10.5로 업그레이드하는 방법에 대해 설명합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions">모든 Adobe Commerce 버전에서 Google Maps 액세스 손실에 대한 수정된 패치:</a> 이 문서에서는 3.54 이상의 최신 Google Maps 버전과 호환되지 않는 Adobe Commerce 판매자를 위한 수정 사항을 제공합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">Adobe Commerce - APSB24-40에 보안 업데이트를 사용할 수 있습니다.</a> 이 문서에서는 CVE-2024-34102 관련 업데이트를 공유합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments">통합 환경의 성능 저하:</a> 이 문서에서는 Pro 통합 환경 및 스타터 스테이징 환경의 성능이 낮은 문제에 대한 해결 방법을 제공합니다. 
    </td>
    <td>새 문서 </td>
    <td>2024년 7월 30일</td>
 </tr>
</table>

## 인기 있는 문서

* [Cloud 2.4.4의 Adobe Commerce OpenSearch로 전환](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Adobe Commerce의 Apache log4j2 취약성](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Adobe Commerce APSB22-12에서 사용할 수 있는 보안 업데이트](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [클라우드 인프라에서 Adobe Commerce의 중단을 식별하고 측정합니다.](/help/how-to/general/how-to-identify-outages.md)
* [Adobe Commerce에서 클러스터의 환경 vCPU 계층 보기](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [클라우드 인프라의 Adobe Commerce: CPU 할당 계산](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [클라우드 인프라의 Adobe Commerce: 호스트의 CPU 구성 확인](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
