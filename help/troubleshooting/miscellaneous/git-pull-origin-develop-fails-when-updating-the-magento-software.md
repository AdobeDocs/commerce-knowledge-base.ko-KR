---
title: Adobe Commerce 소프트웨어를 업데이트할 때 git 가져오기 원본 개발에 실패함
description: 이 문서에서는 'git 가져오기 원본 개발'을 실행할 때 Adobe Commerce 소프트웨어를 업데이트할 수 없는 경우에 대한 수정 사항을 제공합니다.
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Adobe Commerce 소프트웨어를 업데이트할 때 git 가져오기 원본 개발에 실패함

이 문서에서는 `git pull origin develop`을(를) 실행할 때 Adobe Commerce 소프트웨어를 업데이트할 수 없는 경우에 대한 수정 사항을 제공합니다.

## 세부 사항

Adobe Commerce 소프트웨어를 업데이트하는 단계 중 하나는 를 실행하여 로컬 저장소를 업데이트하는 것입니다.

```bash
$ git pull origin develop
```

다음 오류가 표시될 수 있습니다.

```terminal
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

덮어쓸 파일을 찾으려면 메시지를 읽거나 다음을 입력합니다.

```bash
git status
```

다음 섹션에서는 제안된 해결 방법에 대해 설명합니다.

### 제안된 해결 방법

해결 방법은 Adobe Commerce 파일 시스템에서 의도적으로 파일을 수정했는지 여부에 따라 다릅니다. 자세한 내용은 다음 섹션 중 하나를 참조하십시오.

#### 의도적으로 파일을 수정했습니다.

일반적인 방법으로 충돌을 수동으로 해결하십시오. 방법을 잘 모를 경우 [GitHub 도움말](https://help.github.com/)을 참조하세요.

#### 의도적으로 파일을 수정하지 않았습니다.

다음 중 하나를 시도해 보십시오.

* 파일을 수정하지 않았으며 Adobe Commerce 파일 시스템에서 변경 사항을 제거하거나 덮어써도 상관이 없는 경우 다음을 입력합니다.

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  그런 다음 Adobe Commerce 업데이트를 사용하지 않던 위치로 계속 진행합니다.

* GitHub 구성 설정을 통해 향후 이러한 오류를 방지할 수 있습니다. 기본적으로 GitHub는 운영 체제 기본 줄 끝 문자를 사용하여 콘텐츠를 저장합니다. Linux를 사용하고 있지만 다른 공동 작업자가 Windows를 사용하여 변경 작업을 수행한 경우 GitHub는 복제하거나 가져올 때 Windows 줄 끝을 Linux로 변환합니다. 이렇게 하면 실제로 변경되지 않았을 때 파일이 변경된 것처럼 보입니다.

  줄 끝을 무시하도록 GitHub를 구성하려면 Git 클라이언트에 다음 명령을 입력합니다.

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Windows를 사용하는 경우 다음을 입력합니다.

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe은 특정 GitHub 구성 설정을 추천하거나 보증하지 않습니다. 앞의 내용은 제안에만 해당됩니다. 자세한 내용은 [GitHub 도움말](https://help.github.com/)을 참조하세요.

  Adobe Commerce 업데이트를 사용하지 않고 계속 진행합니다.
