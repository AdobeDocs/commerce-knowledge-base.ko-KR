---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# 메타데이터 유효성 검사 안내서

MD 파일에서 메타데이터의 올바른 형식을 보장하기 위해 메타데이터 유효성 검사 테스트를 실시했습니다. 이 문서에서는 기여자가 가장 일반적인 메타데이터 유효성 검사 오류 중 일부를 방지하는 데 도움이 되는 지침을 제공합니다.

**메타데이터의 예:**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## 일반적인 유효성 검사 오류 및 이를 방지/수정하는 방법

다음은 메타데이터 유효성 검사 오류가 발생하는 가장 일반적인 시나리오 중 일부입니다.

### 메타데이터의 콜론

제목이나 레이블 중 하나 또는 둘 다에 콜론이 있는 경우 유효성 검사 오류가 발생합니다.

**예:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

이 오류를 방지하려면 제목이나 레이블을 **작은따옴표**&#x200B;로 줄바꿈(또는 둘 다 콜론이 있는 경우 둘 다)하십시오.

**예:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### 메타데이터의 콜론 및 작은따옴표 또는 아포스트로피

제목 또는 레이블에 콜론, 작은따옴표 또는 아포스트로피가 있는 경우 이전 솔루션이 작동하지 않습니다.

**예:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

이 오류는 제목 또는 레이블(또는 둘 다)을 **큰따옴표**&#x200B;로 줄바꿈하여 해결되었습니다.

**예:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### 메타데이터의 콜론, 큰따옴표 및 작은따옴표 또는 아포스트로피

**예:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

이 경우 제목이나 레이블(또는 둘 다)을 **큰따옴표**&#x200B;로 줄바꿈하고 **백슬래시**&#x200B;를 사용하여 제목과 레이블의 모든 큰따옴표를 이스케이프 처리합니다.

**예:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### 메타데이터에 필드 누락

메타데이터에서 제목 필드 또는 레이블 필드가 누락된 경우 유효성 검사 오류가 발생합니다.

**예:**

```markdown
---
title: This is a title
---
```

또는

```markdown
---
labels: article,labels,tags
---
```

이 오류를 방지하려면 메타데이터에 두 필드를 모두 포함하십시오.

레이블 필드는 비워 둘 수 있으며 오류가 발생하지 않지만 제목 필드는 채워야 합니다.

**예:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
