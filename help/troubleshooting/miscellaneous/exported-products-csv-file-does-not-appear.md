---
title: 내보낸 제품 .csv 파일이 표시되지 않음
description: 이 문서에서는 Commerce 관리자의 .csv 파일로 제품을 내보내려고 하지만 파일이 표시되지 않는 문제에 대한 수정 사항을 제공합니다.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: d55702ab97f3770d0ec71322f6c24448f0169ad4
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# 내보낸 제품 .csv 파일이 표시되지 않음

이 문서에서는 Commerce 관리자의 .csv 파일로 제품을 내보내려고 하지만 파일이 표시되지 않는 문제에 대한 수정 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 문제

<u>재현 단계</u>

필수 구성 요소: **URL에 비밀 키 추가** 옵션이 *예*(으)로 설정되어 있습니다. 옵션은 Commerce 관리자의 **스토어** > **구성** > **고급** > **관리자** > **보안**&#x200B;에 구성되어 있습니다.

1. 관리자에서 **시스템** > **데이터 전송** > **내보내기**&#x200B;로 이동합니다.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. 선택
   * **엔터티 형식**: *제품*
   * **파일 형식 내보내기**: *CSV*
   * **필드 엔클로저**: 선택하지 않은 상태로 둡니다.
1. **계속**&#x200B;을 클릭합니다.
1. 다음 메시지가 표시됩니다. *&quot;메시지가 큐에 추가되었습니다. 파일을 가져올 때까지 기다립니다.*.

<u>예상 결과</u>

내보낸 제품이 포함된 .csv 파일이 몇 분 후에 격자에 표시됩니다.

<u>실제 결과</u>

내보낸 제품이 포함된 .csv 파일이 10분 이상 그리드에 표시되지 않습니다.

## 원인

Adobe Commerce 애플리케이션 부품 버전 2.3.2의 내보내기 기능에 대해 알려진 문제입니다.

## 솔루션

이 문제에 대해 두 가지 가능한 솔루션이 있습니다.

* URL에 비밀 키 추가 옵션을 비활성화합니다.
* `bin/magento queue:consumers:start exportProcessor` 명령을 수동으로 실행하고 cron에서 실행되도록 선택적으로 구성합니다.

다음 단락에서 두 옵션에 대한 세부 사항을 참조하십시오.

### URL에 암호 키 추가 옵션 비활성화

1. 관리자에서 **스토어** > **구성** > **고급** > **관리자** > **보안**&#x200B;으로 이동합니다.
1. **URL에 비밀 키 추가** 옵션을 *아니요.*(으)로 설정
1. **구성 저장**&#x200B;을 클릭합니다.
1. **시스템** > **도구** > **캐시 관리**&#x200B;에서 캐시를 정리하거나 실행 중    ```bash    bin/magento cache:clean``` 또는 관리자.

### 내보내기 명령을 수동으로 실행하고 필요에 따라 cron job으로 추가

내보내기 파일을 가져오려면 `bin/magento queue:consumers:start exportProcessor` 명령을 실행합니다. 이 작업을 실행한 후에는 파일이 격자에 표시되어야 합니다.


필요한 경우 프로세스를 cron 작업으로 추가하려면 `.magento.env.yaml` 파일에 `CRON_CONSUMERS` 변수를 추가해야 합니다.

#### 프로세스를 cron 작업으로 추가(선택 사항)

1. cron 이 설정 및 구성되어 있는지 확인하십시오. 자세한 내용은 [cron 작업 설정](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)을 참조하십시오.
1. 다음 명령을 실행하여 메시지 대기열 소비자 목록을 반환합니다.     `./bin/magento queue:consumers:list`
1. 루트 응용 프로그램 디렉터리의 `.magento.env.yaml` 파일에 다음 내용을 추가하고 추가하려는 소비자를 포함하십시오. 예를 들어 내보내기 처리에 필요한 소비자는 다음과 같습니다.

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   그런 다음 이 업데이트된 파일을 푸시하고 환경을 다시 배포합니다. 개발자 설명서에서 [프로젝트에 사용자 지정 크론 작업을 추가](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project)도 참조하십시오.

>[!NOTE]
>
>환경에 대한 `.magento.env.yaml` 파일을 찾을 수 없고 파일이 삭제되었다고 생각되면 새 `.magento.env.yaml`을(를) 만들어야 합니다. 처음에는 비어 있을 수 있으므로 필요에 따라 정보를 추가할 수 있습니다. 개발자 설명서에서 [배포를 위한 환경 변수 구성](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) 및 [환경 변수 구성](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) 문서를 참조하십시오.

>[!TIP]
>
>[YAML 파일](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)은(는) 대/소문자를 구분하므로 탭을 허용하지 않습니다. .magento.env.yaml 파일 전체에서 일관된 들여쓰기를 사용해야 합니다. 그렇지 않으면 구성이 예상대로 작동하지 않을 수 있습니다. 설명서와 샘플 파일의 예제에서는 두 개의 공백 들여쓰기를 사용합니다. ece-tools validate 명령을 사용하여 구성을 확인합니다.

>[!NOTE]
>
>Adobe Commerce on cloud infrastructure Pro 프로젝트에서 `.magento.app.yaml`을(를) 사용하여 스테이징 및 프로덕션 환경에 사용자 지정 cron 작업을 추가하려면 먼저 Adobe Commerce on cloud infrastructure에서 [auto-cron 기능](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab)을(를) 활성화해야 합니다. 이 기능이 활성화되어 있지 않으면 [지원 티켓을 만들어](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 작업을 추가하세요.
