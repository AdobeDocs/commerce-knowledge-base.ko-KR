---
title: 사용자 정의 SSL 인증서 만료 정보
description: 이 문서에서는 Adobe 정의 SSL 인증서가 사용자가 제공한 SSL 인증서로 업데이트된 경우에 대한 솔루션을 제공합니다.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 사용자 정의 SSL 인증서 만료 정보

이 문서에서는 Adobe 정의 SSL 인증서가 사용자가 제공한 SSL 인증서로 업데이트된 경우에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

Adobe Commerce은 만료 30일 전에 SSL 인증서를 자동으로 업데이트합니다. 이 자동화는 교체되는 인증서가 내부 SSL인지 또는 사용자 지정 타사 SSL인지 여부를 확인하지 않으며, 만료 감지 시 유효한 내부 SSL로 교체합니다. 이렇게 하면 사이트에 사용자 정의 인증서가 있어야 하는 사이트 소유자 및 운영자는 물론, 사이트 중단을 비롯한 다른 기능 문제에 대한 잠재적인 혼동을 일으킬 수 있습니다.

<u>재현 단계</u>

1. 웹 사이트에 설치된 사용자 정의 SSL 인증서.
1. 자동화는 사용자 정의 SSL 인증서가 30일 후에 만료됨을 감지합니다.
1. Adobe Commerce은 사용자 정의 인증서를 내부 인증서로 자동으로 바꿉니다.

<u>예상 결과</u>

Adobe Commerce은 자동화된 SSL 인증서 업데이트를 실행할 때 사용자 정의 인증서를 건너뜁니다.

<u>실제 결과</u>

Adobe Commerce은 만료 후 30일이 경과하면 모든 인증서를 업데이트합니다.

## 솔루션

판매자가 자체 사용자 정의 SSL 인증서를 사용하도록 선택하는 경우 내부 Adobe Commerce SSL 인증서로 대체되지 않도록 인증서 만료 30일 이상 전에 업데이트해야 합니다.

사용자 지정 SSL이 내부 SSL로 대체되었으며 업데이트된 사용자 지정 SSL 인증서로 대체하려는 경우 새 인증서 파일을 업로드한 위치로 [지원 요청을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오. 새 SSL의 시작 날짜를 포함하십시오. 이 정보가 있으면 새 SSL 인증서를 설치할 수 있습니다.

## 관련 읽기

* 지원 기술 자료의 [Magento Commerce Cloud에 대한 SSL(TLS) 인증서: FAQ](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md).
* 개발자 설명서에서 [명령줄 도구 참조: magento-cloud certificate:add](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd).
* 개발자 설명서에서 [Launch 검사 목록](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/launch/checklist)을 참조하세요.
* 사용 안내서에서 [사이트 전체 분석 도구에 액세스](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool)합니다.
