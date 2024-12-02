---
title: 샌드박스 스크립트로 Adobe Commerce 2 Bootstrap
description: 샘플 샌드박스 스크립트에서 Adobe Commerce 2 애플리케이션을 초기화하려면 Adobe Commerce 루트 디렉토리에서 다음 스크립트를 실행합니다.
exl-id: a6acb30a-5175-42c6-8de3-e80c9ae8dac1
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# 샌드박스 스크립트로 Adobe Commerce 2 Bootstrap

샘플 샌드박스 스크립트에서 Adobe Commerce 2 애플리케이션을 초기화하려면 Adobe Commerce 루트 디렉토리에서 다음 스크립트를 실행합니다.

```php
<?php

error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', 1);

require __DIR__ . '/app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
$objectManager = $bootstrap->getObjectManager();

//$model = $objectManager->get('Vendor\Module\Some\Model');
```
