---
title: 'Adobe Commerce 2.4.0 알려진 문제: 통합 테스트 실패'
description: 이 문서에서는 'Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()' 선언이 2.4.0에 사용되는 PHPUnit 9와 호환되지 않아 통합 테스트가 실패하는 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 알려진 문제: 통합 테스트 실패

이 문서에서는 `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` 선언이 2.4.0에 사용되는 PHPUnit 9와 호환되지 않으므로 통합 테스트가 실패하는 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0

## 문제

<u>재현 단계</u>

2.4.0 통합 테스트를 실행합니다.

<u>예상 결과</u>

테스트가 통과되었습니다.

<u>실제 결과</u>

*PHP에 심각한 오류: Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() 선언은 PHPUnit\\Framework\\TestCase::setUp(): 36행의 /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php에서 void와 호환되어야 합니다*

## 솔루션

이 문서에 제공된 패치를 적용합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0

## 패치 적용 방법

자세한 내용은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
