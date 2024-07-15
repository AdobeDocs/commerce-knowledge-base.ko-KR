---
title: 클라우드 사이트가 느립니다.
description: 이 문서에서는 트래픽 부하가 큰 경우 클라우드 인프라 사이트의 Adobe Commerce을 더 나은 성능으로 만드는 방법과 이 부하를 줄이는 방법에 대한 권장 사항을 제공합니다.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# 클라우드 사이트가 느립니다.

이 문서에서는 트래픽 부하가 큰 경우 클라우드 인프라 사이트의 Adobe Commerce을 더 나은 성능으로 만드는 방법과 이 부하를 줄이는 방법에 대한 권장 사항을 제공합니다.

## 영향을 받는 버전 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

<u>재현 단계</u>

1. Adobe Commerce 스토어를 방문하십시오.
1. 범주 페이지를 탐색합니다.
1. 장바구니에 제품을 추가합니다.

<u>예상 결과</u>

사이트는 응답하고 장바구니에 제품을 추가하는 것은 빠릅니다.

<u>실제 결과</u>

사이트가 느리거나 카테고리 페이지는 빠르지만 장바구니 페이지는 느립니다.

## 디버깅 단계 및 솔루션

다음 단계를 수행하여 성능 저하의 원인을 추적하고 해결합니다. 첫 번째 및 두 번째 단계를 전환할 수 있지만 캐시 설정 최적화가 도움이 되지 않는 경우에만 IP 차단으로 진행합니다.

1. 트래픽이 많은 페이지의 캐시 적중률을 확인하고 많이 업데이트되는 데이터의 양을 줄이십시오.
1. 전체 사이트 캐시 적중률을 확인하고 일반 캐시/Fastly 구성을 확인합니다.
1. 높은 서버 로드를 유발하는 웹 클라이언트를 식별하고 높은 로드를 유발하는 IP를 차단합니다.

다음 단락에서는 각 단계에 대해 자세히 설명합니다.

### 1단계: 트래픽이 많은 페이지에 대한 캐시 적중률 확인

폭주하는 트래픽으로 인해 막힌 사이트를 해결하는 첫 번째 단계는 스토어의 홈 페이지 및 최상위 카테고리 페이지와 같이 가장 많은 트래픽이 발생하는 페이지가 제대로 캐시되도록 하는 것입니다.

Fastly 설명서의 [cURL을 사용한 캐시 확인](https://docs.fastly.com/guides/debugging/checking-cache#using-curl)에 설명된 대로 cURL을 사용한 `X-Cache` HTTP 헤더를 검토하여 이러한 페이지의 캐시 적중률을 확인할 수 있습니다. 또는 즐겨 찾는 웹 브라우저의 개발자 도구 모음에 있는 네트워크 탭을 사용하여 동일한 헤더를 확인합니다.

Fastly는 일반적으로 애플리케이션에서 들어오는 응답 헤더를 준수하지만, 헤더가 모두 &quot;캐시하지 않음&quot;으로 설정되어 있고 페이지가 &quot;과거에 만료됨&quot;으로 설정되어 있는 경우에는 Fastly가 페이지를 캐시할 수 없습니다.

>[!WARNING]
>
>Fastly는 응답 헤더를 변경하므로 기본 URL을 cURL 또는 웹 브라우저로 확인해도 애플리케이션에서 내보내는 헤더가 반드시 표시되지는 않습니다. Fastly 자체는 &quot;캐시 없음&quot; 헤더가 있는 웹 브라우저에 응답하지만 웹 애플리케이션 자체는 캐싱을 허용하고 Fastly는 항목을 제대로 캐시하는 것이 일반적입니다. 따라서 이 경우 &quot;cache-control&quot; 및 &quot;pragma&quot; 헤더 정보가 유용하지 않습니다.

#### 트래픽이 많은 페이지 문제 해결

인덱스 페이지의 적중률이 낮은 경우 해당 페이지에 있는 많이 업데이트된 데이터의 양을 줄여 수정할 수 있습니다.

### 2단계: 전체 사이트 캐시 적중률 확인

전체 캐시 적중률을 확인하려면 다음을 수행합니다.

1. 클라우드 인프라 환경에서 Adobe Commerce에 대한 [Fastly 자격 증명을 가져옵니다](http://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#cloud-fastly-creds).
1. 다음 Linux/macOS cURL 명령을 실행하여 지난 30분 동안 사이트에 대한 적중률을 확인하고 Fastly 자격 증명에 대한 값으로 및 을 바꿉니다.

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   시간 범위 쿼리 옵션을 `?by=minute`에서 `?by=hour` 또는 `?by=day`(으)로 변경하여 지난 하루 또는 한 달 동안의 히트를 확인할 수도 있습니다. Fastly 캐시 통계를 가져오는 방법에 대한 자세한 내용은 Fastly 설명서에서 [쿼리 옵션](https://docs.fastly.com/api/stats#Query)을 참조하십시오.

   `| json_pp` 옵션은 `json_pp` 유틸리티를 사용하여 JSON 응답 출력을 예쁘게 인쇄합니다. &quot;_&#39;json\_pp 찾을 수 없음&quot;_ 오류가 발생하면 `json_pp` 유틸리티를 설치하거나 다른 명령줄 도구를 사용하여 JSON 예쁜 인쇄를 하십시오. 또는 `| json_pp` 매개 변수를 삭제하고 명령을 다시 실행하십시오. JSON 응답 출력의 형식이 지정되지 않았지만 JSON 뷰티어를 통해 실행하여 정리할 수 있습니다.

적중률이 0.90 또는 90%를 넘으면 전체 페이지 캐시가 작동 중임을 나타냅니다.

적중률이 0.85 또는 85% 미만이면 사이트 구성 문제를 나타내거나, 콘텐츠를 캐시할 수 없는 타사 확장이 설치되어 있을 수 있습니다.

#### 전체 캐시 적중률 문제 해결

1. 시간별 및 일별 적중률 통계를 사용하여 적중률이 감소하기 시작한 시기를 식별합니다. 사이트에 변경 사항을 배포한 시점과 거의 동시에 적중률이 갑자기 떨어진 경우 사이트 로드가 감소할 때까지 변경 사항을 롤백하는 것이 좋습니다.
1. Commerce 관리자의 **스토어** > **구성** > 고급 > **시스템** > **전체 페이지 캐시**&#x200B;에서 구성을 확인하십시오. **공개 콘텐츠에 대한 TTL** 값이 너무 낮게 설정되어 있지 않은지 확인하십시오.
1. [VCL 코드 조각을 업로드했는지](https://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#upload-vcl-snippets)확인하십시오.
1. 사용자 지정 VCL 스니펫을 사용하는 경우 &quot;전달&quot; 또는 &quot;파이프&quot; 작업을 올바르게 사용하도록 디버깅하십시오. 이러한 스니펫은 주의 깊게 사용해야 하며, 최소한 일종의 조건에서 사용해야 합니다. 추가 팁은 개발자 설명서에서 [사용자 지정 Fastly VCL 코드 조각](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-vcl-custom-snippets.html)을 참조하십시오.

### 3단계: 높은 서버 로드를 유발하는 웹 사이트 식별

다음 방법 중 하나를 사용하여 Adobe Commerce 스토어에 액세스하는 IP 주소에 대한 정보를 가져올 수 있습니다.

* SSH 세션을 통해 HTTP 액세스 로그를 확인합니다.
* 사이트에 과부하를 초래하는 IP 주소 목록을 요청하려면 Adobe Commerce 지원 센터에 문의하십시오.

#### HTTP 액세스 로그 확인

사이트의 액세스 로그를 보려면 로컬 개발 환경에서 다음 명령을 실행합니다.

```bash
magento-cloud log access
```

더 많은 줄 보기

```bash
--lines
```

옵션(예: )

```bash
magento-cloud log access --lines=500
```

이 로그를 보고 요청의 많은 부분이 특정 IP 주소에서 오는지 확인할 수 있습니다. 다른 방법은 다음과 같이 로그에서 가장 자주 발생하는 IP 주소를 자동으로 계산하기 위해 `awk` , `sort` 및 `uniq`을(를) 사용하는 것입니다.

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

다음과 같은 경우

```bash
magento-cloud log
```

명령이 작동하지 않습니다. SSH를 사용하여 원격 서버에 연결하고 `/var/log/access.log`에서 로그 파일을 확인할 수 있습니다.

서버 로드가 많은 IP 주소를 식별한 후 **스토어** > **구성** > 고급 > **시스템** > **전체 페이지 캐시** > **빠른 구성** > **차단**&#x200B;에서 Commerce 관리 패널의 IP 차단 목록을 구성하여 차단할 수 있습니다.

과부하로 인해 관리자에 액세스할 수 없는 경우 Fastly API를 사용하여 차단 규칙을 설정할 수 있습니다.

1. [API를 사용하여 ACL 작업](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Fastly 문서에 설명된 대로 ACL을 만듭니다.
1. `recv` 섹션에서 ACL\_NAME\_GOES\_HERE을 이전 단계에서 만든 ACL의 이름으로 바꾼 다음 내용으로 VCL 코드 조각을 만듭니다.

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

IP 주소 차단에 대한 자세한 내용은 GitHub의 [Fastly Adobe Commerce 모듈 안내서](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)를 참조하십시오.
