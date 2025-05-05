---
title: 클라우드 인프라의 Adobe Commerce에서 Fastly 캐싱이 작동하지 않음
description: 이 문서에서는 사이트에서 작동하지 않는 Fastly 캐싱에 대한 수정 사항을 제공합니다. Fastly는 클라우드 인프라 계획 및 구현에 대한 Adobe Commerce에 포함된 CDN 및 캐싱 서비스입니다. Fastly 확장이 작동하는지 확인하거나 Fastly 확장을 디버깅하려면 curl 명령을 사용하여 특정 응답 헤더를 표시할 수 있습니다. 이러한 응답 헤더 값은 Fastly가 활성화되어 제대로 작동하는지 여부를 나타냅니다. 헤더 및 캐싱 동작 값에 따라 문제를 추가로 조사할 수 있습니다.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에서 Fastly 캐싱이 작동하지 않음

이 문서에서는 사이트에서 작동하지 않는 Fastly 캐싱에 대한 수정 사항을 제공합니다. Fastly는 클라우드 인프라 계획 및 구현에 대한 Adobe Commerce에 포함된 CDN 및 캐싱 서비스입니다. Fastly 확장이 작동하는지 확인하거나 Fastly 확장을 디버깅하려면 curl 명령을 사용하여 특정 응답 헤더를 표시할 수 있습니다. 이러한 응답 헤더 값은 Fastly가 활성화되어 제대로 작동하는지 여부를 나타냅니다. 헤더 및 캐싱 동작 값에 따라 문제를 추가로 조사할 수 있습니다.

이 정보는 라이브 사이트 및 원본 서버에 대한 Fastly 헤더를 확인하고 테스트하는 데 도움이 됩니다.

## 영향을 받는 버전

* 클라우드 인프라의 Adobe Commerce
* Fastly 1.2.27 이상

## 문제

라이브 사이트, 프로덕션 또는 스테이징 환경에서 캐싱이 작동하지 않을 수 있습니다.

## 원인

일반적으로 Fastly 캐싱이 작동하지 않는 문제는 구성, 잘못된 자격 증명 또는 지원되지 않는 Adobe Commerce 확장입니다. Fastly를 잘못 설정하거나 헤더를 제거하는 지원되지 않는 확장을 사용하는 경우 Fastly 캐싱이 작동하지 않습니다.

## 명령을 사용하여 테스트 및 응답 헤더 확인

### dig 명령으로 테스트

먼저 URL에 대한 dig 명령이 있는 헤더를 확인합니다. 터미널 응용 프로그램에서 dig `<url>`을(를) 입력하여 헤더에 Fastly 서비스가 표시되는지 확인합니다. 추가 Dig 테스트는 Fastly의 [DNS를 변경하기 전 테스트](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains)를 참조하십시오.

For example:

* 라이브 사이트: `dig http[s]://<your domain>`
* 준비 중: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* 프로덕션: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### curl 명령을 사용하여 테스트

Magento 그런 다음 curl 명령을 사용하여 X-Tag가 있는지, 그리고 추가 헤더 정보가 있는지 확인합니다. 명령 형식은 스테이징 및 프로덕션에 따라 다릅니다.

이러한 명령에 대한 자세한 내용을 보려면 `-H "host:URL"`을(를) 삽입할 때 Fastly를 건너뛰고, 연결 위치에 원본(OneDrive 스프레드시트의 CNAME 정보)으로 바꾸고, `-k`에서 SSL을 무시하며, `-v`에서 자세한 응답을 제공합니다. 헤더가 올바르게 표시되면 라이브 사이트를 확인하고 헤더를 다시 확인합니다.

* Fastly를 우회하여 원본 서버에 직접 연결할 때 헤더 문제가 발생하는 경우 코드, 확장 또는 인프라에 문제가 있을 수 있습니다.
* 원본 서버를 직접 히트하는 오류가 발생하지 않지만 Fastly를 통해 라이브 도메인을 히트하는 헤더가 누락된 경우 Fastly 오류가 발생할 수 있습니다.

먼저 **라이브 사이트**&#x200B;를 확인하여 응답 헤더를 확인합니다. 명령은 응답을 받기 위해 Fastly 확장을 통과합니다. 올바른 헤더를 받지 못한 경우 원본 서버를 직접 테스트해야 합니다. 이 명령은 `Fastly-Magento-VCL-Uploaded` 및 `X-Cache` 헤더의 값을 반환합니다.

1. 터미널에서 다음 명령을 입력하여 라이브 사이트 URL을 테스트합니다.

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   `--resolve`은(는) 라이브 URL이 DNS로 설정되지 않았으며 고정 경로가 설정되어 있지 않은 경우에만 사용합니다. For example:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. 응답 헤더를 확인하여 Fastly가 작동하는지 확인합니다. 이 명령의 출력은 curl 스테이징 및 프로덕션과 유사합니다. 예를 들어 다음 명령을 사용하여 반환된 고유 헤더가 표시되어야 합니다.

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

**스테이징**&#x200B;을 테스트하려면:

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

**프로덕션 부하 분산 장치**&#x200B;를 테스트하려면:

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

**프로덕션 원본 노드**&#x200B;를 테스트하려면:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

직접 원본 노드:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

예를 들어 공개 URL www.mymagento.biz 이 있는 경우 다음과 유사한 명령을 입력하여 프로덕션 사이트를 테스트합니다.

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### 응답 헤더 확인

* 반환된 응답 헤더 및 값을 확인합니다.
* Fastly-Magento-VCL-Uploaded가 있어야 합니다.
* X-Magento-태그가 반환되어야 합니다.
* Fastly-Module-Enabled는 Yes 또는 Fastly 확장 버전 번호여야 합니다.
* X-Cache는 HIT 또는 HIT, HIT이어야 합니다.
* x-cache-hits는 1,1이어야 합니다.
* Cache-Control: max-age는 0보다 커야 합니다.
* 프래그마는 캐시여야 합니다.

Magento 다음 예제는 Pragma, X-Module-Tags 및 Fastly-Module-Enabled에 대한 올바른 값을 보여 줍니다.

curl 명령의 출력은 길어질 수 있습니다. 다음은 요약만 제공합니다.

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## 해결

### Fastly-Module-Enabled가 없습니다.

응답 헤더에서 Fastly-Module-Enabled에 대해 &quot;예&quot;를 받지 않는 경우 Fasty 모듈이 설치 및 선택되었는지 확인해야 합니다.

스테이징 및 프로덕션에서 Fastly가 활성화되어 있는지 확인하려면 Commerce 관리자의 각 환경에 대한 구성을 확인하십시오.

1. /admin (또는 변경된 관리자 URL)이 있는 URL을 사용하여 스테이징 및 프로덕션용 Admin Console에 로그인합니다.
1. 저장소 > 구성 > 고급 > 시스템으로 이동합니다. 스크롤하여 전체 페이지 캐시 를 클릭합니다.
1. Fastly CDN 이 선택되어 있는지 확인합니다.
1. Fastly Configuration 을 클릭합니다. Fastly 서비스 ID 및 Fastly API 토큰을 입력하십시오(Fastly 자격 증명). 스테이징 및 프로덕션 환경에 대해 올바른 자격 증명을 입력했는지 확인합니다. 자격 증명 테스트 를 클릭하여 도움말을 봅니다.
1. composer.json을 편집하고 Fasty 모듈이 버전에 포함되어 있는지 확인합니다. 이 파일에는 버전과 함께 나열된 모든 모듈이 있습니다.

   * &quot;require&quot; 섹션에는 &quot;fastly/magento2&quot;가 있어야 합니다. `<version number>`
   * 저장소 섹션에는 다음 항목이 있어야 합니다.

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. 구성 관리를 사용하는 경우 구성 파일이 있어야 합니다. app/etc/config.app.php(2.0, 2.1) 또는 app/etc/config.php(2.2) 파일을 편집하고 설정 `'Fastly_Cdn' => 1`이(가) 올바른지 확인하십시오. 설정이 `'Fastly_Cdn' => 0`이(가) 아니어야 합니다(사용 안 함).[Fastly]를 사용하도록 설정한 경우 구성 파일을 삭제하고 bin/magento magento-cloud:scd-dump 명령을 실행하여 업데이트하십시오. 이 파일에 대한 자세한 내용은 구성 안내서에서 [시스템별 설정 관리 예제](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=ko#manage-the-system-specific-configuration)를 참조하십시오.

모듈이 설치되지 않은 경우 [통합 환경](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 분기에 설치하여 스테이징 및 프로덕션에 배포해야 합니다. Commerce on Cloud Infrastructure Guide의 지침은 [Set up Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ko)를 참조하십시오.

### Fastly-Magento-VCL-Uploaded가 없습니다.

설치 및 구성 중에 Fastly VCL을 업로드해야 합니다. 이는 사용자가 생성하는 사용자 지정 VCL 스니펫이 아니라 Fastly 모듈에서 제공하는 기본 VCL 스니펫입니다. 자세한 내용은 Commerce on Cloud Infrastructure Guide의 [Upload Fastly VCL snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ko#upload-vcl-to-fastly)을(를) 참조하십시오.

### X-Cache에 누락 포함

X-Cache가 HIT, MISS 또는 MISS, MISS인 경우 동일한 curl 명령을 다시 입력하여 페이지가 캐시에서 최근에 제거되지 않았는지 확인합니다.

동일한 결과를 얻으면 curl 명령을 사용하고 응답 헤더를 확인합니다.

* Pragma가 캐시임
* X-Magento-태그가 있음
* Cache-Control: max-age가 0보다 큼

문제가 지속되면 다른 확장이 이러한 헤더를 재설정할 수 있습니다. 스테이징에서 다음 절차를 반복하여 문제를 일으키는 확장을 비활성화합니다. 문제를 일으키는 확장을 찾으면 프로덕션에서 확장을 비활성화해야 합니다.

1. 확장을 비활성화하려면 Commerce on Cloud Infrastructure 안내서의 [확장 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=ko#manage-extensions) 섹션에 지정된 단계를 따릅니다.
1. 확장을 비활성화한 후 **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**(으)로 이동합니다.
1. **[!UICONTROL Flush Magento Cache]**&#x200B;을(를) 클릭합니다.
1. 이제 한 번에 하나의 확장을 활성화하여 구성을 저장하고 캐시를 플러시합니다.
1. curl 명령을 시도하고 응답 헤더를 확인합니다.
1. 4단계와 5단계를 반복하여 curl 명령을 활성화하고 테스트합니다. Fastly 헤더가 더 이상 표시되지 않으면 Fastly에 문제를 일으키는 확장이 발견되었습니다.

Fastly 헤더를 재설정하는 확장을 격리하면 확장 개발자에게 추가 지원을 요청하십시오. 타사 확장 개발자가 Fastly 캐싱을 사용할 수 있도록 수정 사항 또는 업데이트를 제공할 수 없습니다.

## 자세한 내용은 개발자 설명서를 참조하십시오.

* [Fastly 정보](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=ko)
* [빠르게 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ko)
* [사용자 지정 Fastly VCL 코드 조각](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=ko)
