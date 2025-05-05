---
title: '...'
labels: troubleshooting,...
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# 문제 해결 문서 템플릿

제목은 문제를 간략하게 설명해야 하며 최대 70자를 사용하는 것이 좋습니다.<br/>
(예: &quot;설치 또는 업그레이드 중 메모리 부족 오류&quot;)

메타데이터에 대한 자세한 내용은 [기여 > 메타데이터](../../CONTRIBUTING.md#metadata)를 참조하십시오.

소개 단락 또는 두 단락: 문제에 대한 간략한 개요. 처음 140자는 SEO 용도로 중요합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 x.x.x
* 클라우드 인프라의 Adobe Commerce x.x.x

(*또는 클라우드 또는 온프레미스의 동일한 버전이 영향을 받는 경우 다음과 같이 말할 수 있습니다.*)

Adobe Commerce(모든 배포 메서드) x.x.x

* 영향을 받는 확장 또는 기술(예: Redis, Fastly): x.x.x

## 문제

전체 오류 메시지를 텍스트로 포함하여 문제에 대한 명확한 설명 및 중요한 스크린샷입니다.
로그에서 발견된 경우 상세 정보(예: 로그, 위치)를 제공합니다.

오류 및 로그에서 특정 프로젝트 ID 또는 고객 정보를 제거합니다! 또한 중요한 정보가 스크린샷에 포함되어 있지 않은지 확인하십시오.

문제가 매우 특정 상황에서 발생하는 경우 다음 형식으로 재현 단계, 예상 결과 및 실제 결과를 제공합니다.

<u>재현 단계</u>:

사전 요구 사항: ... (있는 경우).

1. 첫 번째 단계입니다.
1. 두 번째 단계입니다.
1. ....

<u>예상 결과</u>:

Adobe Commerce이 이 작업을 수행합니다.

<u>실제 결과</u>:

Adobe Commerce이 그렇게 합니다.

## 원인

문제가 발생하는 이유. 수정 사항을 설명하지 마십시오. 다음 섹션에 있을 것입니다. 이유가 명확하지 않거나 이 경우 중요하지 않은 경우 이 옵션을 건너뜁니다.

## 솔루션

문제 해결 방법 단계는 번호 매기기 목록을 사용하십시오.
오류 표시 안 함, 배포 작동, 값 변경됨 및 변경 사항 확인 방법 등의 결과를 사용하여 섹션을 완료합니다.

임시 해결 방법이 있는 경우 이 방법 아래에 별도의 섹션으로 지정하십시오.

## 관련 읽기

* 사용 안내서의 [문서 항목](https://experienceleague.adobe.com/ko/docs/commerce-admin/user-guides/home).
* 개발자 설명서의 [문서 항목](https://developer.adobe.com/commerce/docs/). 또한 Cloud용 devdocs와 온-프레미스 사용자를 구분하고 다음과 같이 지정할 수 있습니다. &quot;[Article topic](https://developer.adobe.com/commerce/docs/) in our developer documentation for Adobe Commerce on cloud infrastructure&quot; Adobe Commerce 온-프레미스에 대한 개발자 설명서에 있는 &quot;[문서 항목](https://developer.adobe.com/commerce/docs/)과(와) 비교&quot;
* 지원 기술 자료의 [문서 항목](https://support.magento.com/hc/en-us).
* 모든 관련 리소스(블로그, 포럼, StackOverflow 등)
