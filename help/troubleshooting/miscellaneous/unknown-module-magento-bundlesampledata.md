---
title: 알 수 없는 모듈 Magento_BundleSampleData
description: 이 문서에서는 Adobe Commerce 설치 중 알 수 없는 모듈 오류에 대한 수정 사항을 제공합니다.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# 알 수 없는 모듈 Magento_BundleSampleData

이 문서에서는 Adobe Commerce 설치 중 알 수 없는 모듈 오류에 대한 수정 사항을 제공합니다.

## 문제 {#details}

설치하는 동안 다음과 유사한 메시지가 표시됩니다.

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## 솔루션 {#solution}

다음 각 항목을 한 번에 하나씩 시도한 다음 설치를 다시 시도하십시오.

1. 웹 설치 마법사를 실행합니다. 모듈은 **고급 모듈 구성**&#x200B;에 나열됩니다. **Magento\_BundleSampleData** 모듈을 비활성화하려면 다음 그림과 같이 **Magento\_BundleSampleData** 확인란의 선택을 취소하십시오.

   ![tshoot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. 웹 브라우저에서 브라우저 기록 및 데이터를 모두 지웁니다.
1. Chrome이 있는 경우 사이트와 관련된 모든 브라우저 데이터를 지웁니다.  **설정** > **고급 옵션** > **개인 정보** > **콘텐츠 설정** > **모든 쿠키 및 사이트 데이터**&#x200B;로 이동합니다. 사이트 열에서 Adobe Commerce 서버 주소를 클릭하고 **모두 제거**&#x200B;를 클릭합니다.
