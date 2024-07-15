---
title: 클라우드 인프라에서 Adobe Commerce에 대한 Blackfire 액세스 제거
description: 2020년 4월 11일부터 Blackfire 성능 모니터링에 대한 무료 액세스가 더 이상 Adobe Commerce on cloud infrastructure Pro 계획 아키텍처 또는 Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 구독에 포함되지 않습니다.  더 이상 Blackfire 계정에 로그인할 수 없습니다. Blackfire.io를 통해 직접 라이선스를 구매하여 4월 11일 이후에도 Blackfire을 계속 사용할 수 있다. 해당 날짜까지 Blackfire에서 직접 라이선스를 구입하지 않은 Adobe Commerce 판매자는 Adobe이 제공한 무료 Blackfire 라이선스를 비활성화하게 됩니다. 이와 함께 프로파일러 도구를 사용하여 새 보고서를 만들 수 있는 기능도 비활성화됩니다. 클라우드 인프라에서 호스팅되는 Pro 아키텍처를 사용하는 고객은 여전히 New Relic 인프라를 통해 인프라 성능에 대한 무료 모니터링을 받을 수 있습니다.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# 클라우드 인프라에서 Adobe Commerce에 대한 Blackfire 액세스 제거

2020년 4월 11일부터 Blackfire 성능 모니터링에 대한 무료 액세스가 더 이상 Adobe Commerce on cloud infrastructure Pro 계획 아키텍처 또는 Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 구독에 포함되지 않습니다.  더 이상 Blackfire 계정에 로그인할 수 없습니다. Blackfire.io를 통해 직접 라이선스를 구매하여 4월 11일 이후에도 Blackfire을 계속 사용할 수 있다. 해당 날짜까지 Blackfire에서 직접 라이선스를 구입하지 않은 Adobe Commerce 판매자는 Adobe이 제공한 무료 Blackfire 라이선스를 비활성화하게 됩니다. 이와 함께 프로파일러 도구를 사용하여 새 보고서를 만들 수 있는 기능도 비활성화됩니다. 클라우드 인프라에서 호스팅되는 Pro 아키텍처를 사용하는 고객은 여전히 New Relic 인프라를 통해 인프라 성능에 대한 무료 모니터링을 받을 수 있습니다.

**Blackfire을 계속 사용하려면**:

1. Blackfire이 있는 라이선스를 직접 구입해야 합니다.
1. 그런 다음 이 [단계](https://blackfire.io/docs/integrations/paas/magentocloud)를 사용하여 Blackfire을 설정합니다.
1. 설치에 문제가 있는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 지원을 요청할 수 있습니다. Blackfire 관련 질문이 있는 경우 [support@blackfire.io](mailto:support@blackfire.io)에서 직접 Blackfire 지원 팀에 문의하십시오.

## 배포를 실행할 때 오류가 발생하는 경우:

배포를 실행할 때 Blackfire 관련 오류가 발생하는 경우 다음을 수행하십시오.

1. 구성에서 Blackfire을 제거합니다. `.magento.app.yaml` 파일을 편집하고 런타임 섹션에서 Blackfire을 제거합니다.

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. 로컬 개발 환경에서 이를 완료하고 클라우드로 푸시합니다.

배포를 실행한 후 다음 오류가 표시되는 경우에만 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)합니다.

*PHP 경고: PHP 시작: 동적 라이브러리 &#39;blackfire.so&#39;를 로드할 수 없음(시도: /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so: 공유 개체 파일을 열 수 없음: 해당 파일 또는 디렉터리가 없음), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so: 공유 개체 파일을 열 수 없음: 해당 파일 또는 디렉터리가 없음). Unknown on line 0*

이 오류는 Blackfire 플러그인을 업데이트하고 로드를 중지해야 함을 의미합니다.

**New Relic 인프라를 사용하려는 경우**:

New Relic 인프라에 액세스하는 방법에 대한 자세한 내용은 지원 기술 자료에서 [New Relic 액세스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html)를 참조하십시오.
