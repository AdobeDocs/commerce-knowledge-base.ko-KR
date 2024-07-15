---
title: 종속성 혼동 공격에 대한 작성기 플러그인
description: 이 문서에서는 종속성 혼동 공격을 위해 릴리스된 작성기 플러그인에 대한 정보와 오류 방지에 대한 권장 사항을 제공합니다. Composer 플러그인은 Adobe Commerce 2.4.3 릴리스와 함께 도입되어 종속성 혼동 공격으로부터 Adobe Commerce 판매자를 보호합니다.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# 종속성 혼동 공격에 대한 작성기 플러그인

이 문서에서는 종속성 혼동 공격을 위해 릴리스된 작성기 플러그인에 대한 정보와 오류 방지에 대한 권장 사항을 제공합니다. Composer 플러그인은 Adobe Commerce 2.4.3 릴리스와 함께 도입되어 종속성 혼동 공격으로부터 Adobe Commerce 판매자를 보호합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.3 및 이후 버전(모든 배포 방법)

## 문제

작성기 설치/업데이트 중에 작성기 플러그 인 `magento/composer-dependency-version-audit-plugin`에 의해 `composer.json`에 정의된 직접 또는 간접 종속성 중 적어도 하나를 통해 활성 종속성 혼동 공격의 잠재적 사례가 감지되었습니다.

<u>재현 단계</u>:

작성기를 설치/업데이트할 때 작성기 플러그인이 잠재적인 종속성 혼동 공격을 감지하면 프로세스를 중지합니다. 이 경우 작성기 설치/업데이트는 실패하고 다음과 유사한 오류 메시지가 표시됩니다.

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## 원인

종속성 혼동 공격은 종속성 관리자(예: PHP 작성기)를 속여 원본 패키지가 아닌 공용 소스에서 악성 패키지를 개인 저장소에서 다운로드하도록 하여 서버에서 임의의 코드를 원격으로 실행할 수 있도록 합니다.

공격자가 원래 패키지의 기능을 유지할 수 있는 경우 이러한 공격이 감지되지 않을 수도 있습니다.

공격자는 패키지가 개인 리포지토리를 통해서만 사용할 수 있지만 공개 리포지토리에 등록되지 않은 경우 이 취약성을 악용할 수 있습니다. 그런 다음 공격자는 동일한 이름의 패키지를 공용 저장소에 업로드하고, 사적으로 사용할 수 있는 버전보다 높은 버전을 제공합니다. 그런 다음 종속성 관리자는 비공개 및 공개적으로 사용 가능한 패키지의 버전을 비교하고 공용 리포지토리에서 가장 높은 버전을 선택합니다. 종속성 관리자에서 다운로드한 악성 코드는 애플리케이션 코드와 동일한 권한으로 실행됩니다.

## 솔루션

### Recommendations - 판매자

* 플러그인이 작성기 설치/업데이트를 심각하게 중단할 때 표시되는 오류 메시지를 확인하고 손상될 수 있는 패키지를 인식하는 경우 확장 개발자에게 문의하십시오.
* 마켓플레이스 또는 신뢰할 수 있는 다른 개인 저장소에서 안전한 버전의 패키지를 사용하여 Adobe Commerce을 설치할 수 있습니다.
* 작성기 설치/업데이트를 진행하려면 composer.json에서 필요한 패키지 버전을 마켓플레이스에 있는 정확한 버전으로 변경하십시오.

### 확장 개발자의 기대 사항

* 공용 리포지토리의 경우 플러그인에 대한 패키지가 손상되었는지 여부를 확실히 알 수 있는 방법이 없습니다. 이 플러그인은 packagist.org에 있는 패키지의 공개 버전이 [repo.magento.com](https://repo.magento.com)과(와) 같은 개인 리포지토리에서 사용할 수 있는 버전보다 높은 버전을 사용하는 경우를 검색합니다. 확장 개발자는 이러한 상황을 피하고 [repo.magento.com](https://repo.magento.com)을 통해 사용 가능한 버전보다 최신 버전을 공개적으로 게시하지 않는 것이 좋습니다.
* Adobe Commerce은 Marketplace 검토 프로세스로 인해 확장 릴리스 가용성이 지연될 수 있다는 것을 알고 있지만 이 프로세스는 판매자를 안전하게 보호하고 확장 개발자가 놓쳤을 수 있는 우발적인 실수를 발견할 수 있도록 지원하기 위한 것입니다.
