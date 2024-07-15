---
title: Magento GitHub 저장소를 복제할 수 없음
description: 이 문서에서는 Magento GitHub 리포지토리를 복제할 수 없는 경우에 대한 수정 사항을 제공합니다.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Magento GitHub 저장소를 복제할 수 없음

이 문서에서는 Magento GitHub 리포지토리를 복제할 수 없는 경우에 대한 수정 사항을 제공합니다.

## 세부 사항 {#detail}

오류는 다음과 유사합니다.

```terminal
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## 솔루션 {#solution}

[GitHub 도움말 페이지](https://help.github.com/articles/generating-ssh-keys)에서 설명한 대로 SSH 키를 GitHub에 업로드합니다.
