---
title: ''' [!DNL OpenSearch] 설치''에도 불구하고 ''[!DNL Elasticsearch]''이(가) 검색 엔진으로 표시됩니다.'
description: 이 문서에서는  [!DNL OpenSearch]을(를) 설치하거나 업그레이드한 후에도  [!DNL Elasticsearch] 이(가) 클라우드에서 Adobe Commerce의 검색 엔진으로 계속 표시되는 문제에 대한 해결 방법을 제공합니다.
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# [!DNL OpenSearch] 설치에도 불구하고 [!DNL Elasticsearch]이(가) 검색 엔진으로 표시됨

이 문서에서는 [!DNL OpenSearch]을(를) 설치하거나 (으)로 업그레이드한 후에도 [!DNL Elasticsearch]이(가) 클라우드에서 Adobe Commerce의 검색 엔진으로 표시되는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 버전

cloud 2.4.3-p2 - 2.4.5-p6의 Adobe Commerce

>[!NOTE]
>
>[!DNL OpenSearch]은(는) Adobe Commerce 2.4.6부터 검색 엔진으로 사용할 수 있습니다.

## 문제

[!DNL OpenSearch]을(를) 설치하거나 (으)로 업그레이드한 후에도 [!DNL Elasticsearch]은(는) 클라우드에서 Adobe Commerce에 대한 검색 엔진으로 계속 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**(으)로 이동합니다.
1. 검색 엔진을 확인합니다. [!DNL Elasticsearch7]이(가) 표시됩니다.

## 원인

Adobe Commerce은 [!DNL Elasticsearch7]을(를) 검색 엔진으로 지정하도록 하드 코딩되어 있습니다.

이는 설치된 서비스 버전과 혼동하지 않습니다. 기본 [!DNL OpenSearch] 서비스를 백엔드의 엔진으로 사용하더라도 응용 프로그램은 [!DNL Elasticsearch7]은(는) 검색 엔진으로만 인식하지만 [!DNL OpenSearch]은(는) 인식하지 않습니다.

## 솔루션

[!DNL OpenSearch]이(가) 설치되었는지 확인하려면 다음 명령을 실행하십시오.

**메서드 1**:

* 서버에서 `curl 127.0.0.1:9200` 명령을 실행합니다. 해당 버전과 함께 [!DNL OpenSearch]을(를) 반환해야 합니다.

예:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**메서드 2**:

* Magento 클라우드 CLI에서 `magento-cloud relationships -p <project_id>` 명령을 사용합니다. 명령을 사용한 후 [!DNL OpenSearch]을(를) 찾습니다.

## 관련 읽기

Commerce on Cloud Infrastructure 안내서의 [OpenSearch 서비스 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html).
