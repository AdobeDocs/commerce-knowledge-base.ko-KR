---
title: Magento GitHub 저장소를 복제할 수 없음
description: 이 문서에서는 Magento GitHub 리포지토리를 복제할 수 없는 경우에 대한 수정 사항을 제공합니다.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%
---
# Magento GitHub 저장소를 복제할 수 없음

이 문서에서는 Magento GitHub 리포지토리를 복제할 수 없는 경우에 대한 수정 사항을 제공합니다.

## 세부 사항 {#detail}

오류는 다음과 유사합니다.

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## 솔루션 {#solution}

[GitHub 도움말 페이지](https://help.github.com/articles/generating-ssh-keys)에서 설명한 대로 SSH 키를 GitHub에 업로드합니다.
