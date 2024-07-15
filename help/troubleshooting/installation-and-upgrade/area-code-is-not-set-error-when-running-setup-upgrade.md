---
title: '" setup:upgrade 실행 시 "영역 코드가 설정되지 않음" 오류 발생"'
description: 이 문서에서는 setup:upgrade 명령을 실행할 때 *영역 코드가 설정되지 않음* 오류와 관련된 클라우드 인프라 2.2.3의 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# `setup:upgrade`을(를) 실행할 때 &#39;영역 코드가 설정되지 않음&#39; 오류 발생

이 문서에서는 다음 명령을 실행할 때 *&quot;영역 코드가 설정되지 않음&quot;* 오류 가져오기와 관련된 Cloud Infrastructure 2.2.3의 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.

```bash
setup:upgrade
```

>[!NOTE]
>
>Adobe Commerce 2.2.4에서 문제가 해결되었습니다.

## 문제

실행 시

```bash
bin/magento setup:upgrade
```

명령에 다음 오류 메시지가 표시됩니다. *&quot;모듈 &#39;Magento\_AdvancedSalesRule&#39;: 데이터 설치 중...영역 코드가 설정되지 않음: 세션을 시작하기 전에 영역 코드를 설정해야 합니다.*. 명령 실행이 중단됩니다. 이 문제는 영역 구성이 실제로 설정되기 전에 요청되기 때문에 나타납니다. 패치를 사용하면 오류를 처리할 수 있으며 업그레이드 프로세스를 중단할 수 없습니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch 다운로드](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.2.3

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce 온 클라우드 인프라 및 Adobe Commerce 온-프레미스 2.2.0 - 2.2.3

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
