---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# KB 레이블 안내서

이 문서에서는 Adobe Commerce 지원 기술 자료에서 문서에 레이블을 추가하는 방법에 대한 지침을 제공합니다.
레이블(태그라고도 함)을 사용하면 [Adobe Commerce 지원 기술 자료](https://support.magento.com/hc/en-us)에서 검색 환경을 향상시킬 수 있습니다.
문서 파일의 메타데이터 섹션에 있는 &quot;레이블&quot; 필드에 쉼표로 구분하여 레이블이 추가되며, 쉼표와 다음 레이블 사이에는 공백이 없습니다.
자세한 내용은 [../../.github/CONTRIBUTING.md#metadata]을(를) 참조하십시오.

## 일반 규정

각 문서에 대해 다음 레이블 유형을 추가합니다.

* 제품에 대한 레이블입니다. (필수)
* 영향을 받는 버전의 레이블입니다. (일반 지원 관련 문서를 제외한 필수 항목)
* 콘텐츠 유형에 대한 레이블입니다. (필수)
* 주요 기술 구성 요소에 대한 레이블입니다.(해당되는 경우)
* 문제 해결/설명 중인 프로세스/기능에 대한 레이블입니다. (해당되는 경우)
* 수정/설명 중인 문제에 대한 레이블입니다. (해당되는 경우)

이러한 각 레이블 유형의 레이블을 정의하는 방법에 대한 자세한 권장 사항은 아래 섹션을 참조하십시오.

## 제품 레이블

<table>
<tbody>
  <tr>
    <th>제품 이름</th>
    <th>레이블</th>
  </tr>
  <tr>
    <td>Adobe Commerce(모든 배포 메서드) </td>
    <td>
    "Adobe Commerce,cloud infrastructure,on-premise"
    </td>
  </tr>
  <tr>
    <td>클라우드 인프라의 Adobe Commerce</td>
    <td>
      "Adobe Commerce,cloud infrastructure"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce 온-프레미스</td>
    <td>"Adobe Commerce, 온-프레미스"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence(MBI)</td>
    <td>
        "Magento Business Intelligence, MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce용 B2B</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>Adobe Commerce PWA</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Venia storefront 프로젝트</td>
    <td>"Venia"</td>
  </tr>
  <tr>
    <td>품질 패치 도구, QPT</td>
    <td>"품질 패치 도구, QPT 패치"</td>
  </tr>
  </tbody>
</table>

## 제품 버전의 레이블

* Adobe Commerce의 각 버전에 대해 별도의 레이블을 추가합니다. 예: &quot;2.3.7&quot;
* 간격에 레이블을 추가하지 마십시오.
즉, 영향을 받는 경우 2.3.0-2.3.5이면 &quot;2.3.0, 2.3.1, 2.3.2, 2.3.2-p2, 2.3.3, 2.3.3-p1, 2.3.4, 2.3.4-p2, 2.3.5-p1, 2.3.5-p2&quot;를 추가합니다.
&quot;2.3.0-2.3.5&quot; 아님
* .x로 레이블을 추가하지 마십시오. 예: &quot;2.3.x&quot;

## 콘텐츠 유형에 대한 레이블(범주 기반)

<table>
  <tbody>
    <tr>
      <th>범주</th>
      <th>레이블</th>
    </tr>
    <tr>
      <td>우수 사례</td>
      <td>"우수 사례"("우수 사례" 또는 "우수 사례"가 아님)</td>
    </tr>
    <tr>
      <td>
        문제 해결
      </td>
      <td>
      "문제 해결"
      </td>
    </tr>
    <tr>
      <td>방법</td>
      <td>"방법"</td>
    </tr>
    <tr>
      <td>FAQ</td>
      <td >"FAQ"</td>
    </tr>
  </tbody>
</table>

## 주요 기술 구성 요소 레이블

* 구성 요소의 공식 이름에 따라 대소문자를 사용합니다.
* 하나의 구성 요소에 대해 하나의 레이블인 동의어를 사용하지 마십시오.
* 한 단어 레이블이 선호되지만 구성 요소 이름에 여러 단어가 포함된 경우 여러 단어를 사용하십시오. 문제 설명을 추가하지 마십시오. 즉, &quot;Elasticsearch 문제&quot; 대신 &quot;Elasticsearch&quot;을 넣습니다.
* 콘텐츠가 구성 요소의 특정 버전에만 관련이 있는 경우 - 이름 + 버전을 포함하는 레이블을 추가합니다.\
  예: &quot;Elasticsearch 5&quot;. 여러 특정 버전과 관련이 있는 경우 이 유형의 레이블을 몇 개 추가합니다. 예: &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. 관련성이 있는 경우 여러 버전에 대해 &quot;x&quot;를 사용하십시오. 예: &quot;Elasticsearch 2.x&quot;

예:

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* &quot;웹 설치 마법사&quot;

## 문제 해결/설명 중인 프로세스/기능의 레이블

* 적절한 명사는 제외하고 소문자를 사용하십시오.
* 하나의 엔티티에 대해 하나의 레이블인 동의어를 사용하지 마십시오.
* 단어 레이블은 하나면 더 좋습니다. 문제 설명을 추가하지 마십시오. 즉, &quot;데이터베이스 충돌&quot; 대신 &quot;데이터베이스&quot;를 넣습니다.

예: 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;deployment&quot;
* &quot;대량 업데이트&quot;

## 수정/설명 중인 문제에 대한 레이블

* 적절한 명사는 제외하고 소문자를 사용하십시오.
* 하나의 엔티티에 대해 하나의 레이블인 동의어를 사용하지 마십시오.
* 단어 레이블은 하나면 더 좋습니다. 오류 메시지를 레이블로 변환하지 마십시오.

예:

* &quot;사이트 다운&quot;
* &quot;500 오류&quot;
* &quot;stuck cron&quot;
