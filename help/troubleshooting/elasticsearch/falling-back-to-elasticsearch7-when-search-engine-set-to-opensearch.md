---
title: 검색 엔진이  [!DNL Opensearch] (으)로 설정된 경우  [!DNL Elasticsearch7] (으)로 폴백
description: 이 문서에서는 *Adobe Commerce에서  [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] 로 폴백 시 발생하는 문제에 대한 해결 방법을 제공합니다.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: d17af0f8f92726aa5a6914fc9e1ff13268256d04
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# 검색 엔진이 [!DNL Opensearch]&#x200B;(으)로 설정된 경우 [!DNL Elasticsearch7]&#x200B;(으)로 폴백

이 문서에서는 검색 엔진이 Adobe Commerce에서 [!DNL OpenSearch]&#x200B;(으)로 설정되어 있을 때 *다시[!DNL Elasticsearch7]* 오류가 발생하는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 버전

클라우드 인프라의 Adobe Commerce
2.4.4 - 2.4.4-p12
2.4.5 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch]은(는) Adobe Commerce 2.4.6, 2.4.5-p12, 2.4.4-p13부터 검색 엔진으로 사용할 수 있습니다.

## 문제

**검색 엔진**&#x200B;을(를) **[!DNL OpenSearch]**(으)로 설정했지만 `var/log/support_report.log` 파일에 다음과 같은 유형의 오류가 있습니다.

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>재현 단계</u>:

1. 다음 명령을 실행하여 [!DNL OpenSearch]이(가) 설치되어 있는지 확인하십시오. `curl 127.0.0.1:9200`<br>
*1.2.4*&#x200B;을(를) 나타내는 경우 [!DNL OpenSearch]이(가) 이미 설치되어 있습니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**(으)로 이동합니다.
1. 검색 엔진을 확인합니다. [!DNL Elasticsearch7]이(가) 표시됩니다.

## 원인

사용 중인 버전에서 [!DNL OpenSearch]을(를) 지원하지만 응용 프로그램에서 [!DNL Elasticsearch7]을(를) 검색 엔진으로만 인식/수락합니다.

Adobe Commerce 버전 2.4.6부터 [!DNL OpenSearch]을(를) 검색 엔진으로 선택할 수 있도록 응용 프로그램이 업데이트되었습니다.
클라우드가 아닌 환경에서 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**(으)로 이동하면 아래 **솔루션**&#x200B;에 표시된 대로 이 옵션을 변경할 수 있습니다.
(참고: 클라우드 환경에서는 검색 엔진이 `app/etc/env.php` 파일에서 잠겨 있으므로 이 필드를 변경할 수 없습니다.)

## 솔루션

`.magento.env.yaml` 파일에서 `SEARCH_CONFIGURATION` 변수를 업데이트하고 **검색 엔진**&#x200B;이(가) *[!DNL elasticsearch7]*(으)로 설정되어 있는지 확인하십시오.

## 관련 읽기

Commerce on Cloud Infrastructure 안내서의 [OpenSearch 서비스 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html?lang=ko).
