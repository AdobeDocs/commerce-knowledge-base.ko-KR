---
title: 상단 탐색 패널이 상점 앞에 로드되지 않음
description: 이 문서에서는 캐싱에 바니시를 사용하는 경우 특정 페이지의 콘텐츠(일반적으로 상단 탐색 패널)가 상점 전면에 표시되지 않는 ESI(바니시 Edge Side Includes) 문제에 대한 구성 솔루션을 제공합니다.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 상단 탐색 패널이 상점 앞에 로드되지 않음

이 문서에서는 캐싱에 바니시를 사용하는 경우 특정 페이지의 콘텐츠(일반적으로 상단 탐색 패널)가 상점 전면에 표시되지 않는 ESI(바니시 Edge Side Includes) 문제에 대한 구성 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.X.X
* 모든 바니시 버전

## 문제

<u>필수 구성 요소</u>:

Adobe Commerce 스토어에 대한 Vannish를 설치하고 구성합니다.

<u>재현 단계</u>:

1. 가게 앞쪽으로 가보세요
1. 저장소 페이지를 탐색합니다.

<u>예상 결과</u>:

모든 콘텐츠 및 모든 페이지 블록이 성공적으로 로드되었습니다.

<u>실제 결과</u>:

범주가 있는 상단 탐색 패널과 같은 일부 콘텐츠 블록이 로드되지 않습니다. 대신 공백이 표시됩니다.

## 원인

가능한 문제 원인은 다음과 같습니다.

* ESI에는 HTTPS 액세스 프로토콜을 통해 생성되는 태그가 포함되며, Varnish는 HTTP에서만 작동합니다.
* 바니시는 JSON 내에서 ESI를 처리하지 않습니다.
* 응답 헤더가 Vannish에 비해 너무 커서 처리할 수 없습니다.

## 솔루션

이 문제를 해결하려면 추가 바니시 구성을 수행한 다음 바니시를 다시 시작해야 합니다.

1. `root` 권한이 있는 사용자는 텍스트 편집기에서 Vanish 구성 파일을 엽니다. 다른 운영 체제에 대해 이 파일이 있는 위치에 대한 자세한 내용은 개발자 설명서에서 [바니시 시스템 구성 수정](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/cache/config-varnish-server)을 참조하십시오.
1. `DAEMON_OPTS variable`에서 `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check`을(를) 추가합니다. 이는 다음과 같습니다.

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. VCL 구성 파일에서 다음 매개 변수의 값을 늘려 응답 헤더를 늘립니다. `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. 마지막 두 개의 값이 유사한지 확인합니다.
1. 이 항목을 변경할 때 변경 내용을 적용하려면 `service varnish restart`을(를) 실행해야 합니다.

## 관련 읽기

* 개발자 설명서에서 [Varnish 및 웹 서버를 구성](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/cache/config-varnish-server)합니다.
* [니스용 설명서](https://varnish-cache.org/docs/5.1/reference/index.html)
