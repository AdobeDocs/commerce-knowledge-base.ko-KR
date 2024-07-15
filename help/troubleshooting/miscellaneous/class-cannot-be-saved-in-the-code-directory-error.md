---
title: '"클래스를 코드 디렉터리에 저장할 수 없습니다" 오류"'
description: 이 문서에서는 종속성을 지정하는 방식으로 인해 클래스가 즉시 자동 생성되지 않고 *"클래스가 생성된/코드 디렉터리에 저장될 수 없음"* 오류 메시지가 표시되는 문제를 해결하는 방법에 대해 설명합니다.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# &quot;클래스를 코드 디렉터리에 저장할 수 없습니다&quot; 오류

이 문서에서는 종속성을 지정한 방식으로 인해 클래스가 즉시 자동 생성되지 않고 *&quot;클래스가 생성된/코드 디렉터리&quot;* 오류 메시지가 표시되는 문제를 해결하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* cloud infrastructure 2.2.0 이상 버전의 Adobe Commerce

## 문제

<u>재현 단계</u>

1. 로컬 환경에서 자동 생성된 클래스에 종속된 사용자 지정 클래스를 작성합니다.
1. 사용자 지정 클래스가 트리거되는 시나리오를 실행하고 제대로 작동하는지 확인합니다.
1. 통합 환경에 변경 사항을 커밋하고 푸시합니다. 이렇게 하면 배포 프로세스가 트리거됩니다. 배포가 완료되었습니다.
1. [통합 환경](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)에서 사용자 지정 클래스가 트리거되는 시나리오를 실행합니다.

<u>예상 결과</u>

모든 것이 로컬 환경과 동일한 방식으로 올바르게 작동합니다.

<u>실제 결과</u>

클래스를 `generated/code` 디렉터리에 저장할 수 없다는 오류 메시지가 표시되면서 오류가 발생했습니다.

## 원인

배포 완료 후 `generated/code` 디렉터리를 쓰기에 사용할 수 없으므로 종속성이 있는 클래스가 배포 중에 생성되지 않으며 클래스를 트리거할 때 나중에 바로 생성할 수 없는 것이 문제의 원인입니다.

이러한 상황이 발생할 수 있는 이유는 두 가지가 있습니다.

* 사례 1: 자동 생성된 클래스에 대한 종속성이 있는 클래스가 배포 중에 종속성에 대해 검사되지 않는 진입점( 예: `index.php`)에 있습니다.
* 사례 2: 자동 생성된 클래스에 대한 종속성이 직접 지정됩니다(종속성을 선언하는 생성자의 권장 사용과 비교).

## 솔루션

두 가지 경우에 대한 한 가지 일반적인 해결 방법은 자동 생성된 클래스 대신 실제 팩토리를 만드는 것입니다.

또는 각 사례에 대한 특정 솔루션이 있습니다.

### 사례 1 특정 솔루션

진입점에서 별도의 모듈로 클래스 코드를 이동한 다음 진입점에서 사용합니다.

<u>예</u>

원본 코드(예: `index2.php`:

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

다음 단계를 수행해야 합니다.

1. 클래스 정의를 `app/code/YourVendor/YourModule`(으)로 이동:

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. 다음과 같이 표시되도록 진입점 `my_api/index.php`을(를) 편집합니다.

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### 사례 2 특정 솔루션

종속성 선언을 생성자로 이동합니다.

<u>예</u>

원래 클래스 선언:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

생성자를 다음과 같이 변경해야 합니다.

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## 관련 읽기

* 개발자 설명서에서 [코드 생성](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/code-generation.html).
