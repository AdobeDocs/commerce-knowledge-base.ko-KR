---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# KB Formatting 안내서

## Markdown 작성자

일반적으로 [Adobe Experience League Markdown 구문 스타일 가이드](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=ko)를 사용하지만 몇 가지 차이점과 예외가 있습니다. 또한 경우에 따라 특정 HTML 태그가 필요합니다.

다음은 보고서에서 가장 일반적으로 사용되는 Markdown 서식의 예입니다.

## 기본 서식

텍스트 서식을 굵게 지정하려면 두 개의 별표로 묶습니다.

`This will be **bold** text`

텍스트 서식을 기울임꼴로 지정하려면 한 개의 별표를 사용합니다.

`This text will be *italics*`

밑줄로 텍스트 서식을 지정하려면 `<ins>` 태그를 사용하십시오.

`<ins>This text will be underlined</ins>`

줄 바꿈을 추가하려면 `<br>` HTML 태그를 사용하십시오.


## 헤더

H2에서 H5까지의 헤더에 대해 다음 서식을 사용합니다. 문서 제목은 H1으로 간주되므로 H1은 사용되지 않습니다.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## 인라인 및 블록 코드

단일 백틱을 사용하여 강조 표시할 코드 요소를 묶습니다.

텍스트 단락 내의 \`inline code\`입니다.

### 코드 블록

코드 블록을 삽입하려면 코드 블록을 삼중 백틱으로 묶고 삼중 백틱을 연 후 언어를 지정합니다.

\`\`\` sql

TABLE_NAME을 `Table`(으)로 선택합니다.
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024)(`Size (MB)`)
FROM 정보_스키마.테이블
여기서 TABLE_SCHEMA = &quot;%project_id%&quot;
(DATA_LENGTH + INDEX_LENGTH) 내림차순;

\`\`\`

이 값은 다음과 같이 렌더링됩니다.

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

링크 규칙에 따라 코드 블록에 대한 언어를 항상 지정해야 합니다.

지원되는 언어 목록은 https://github.com/github/linguist/blob/master/lib/linguist/languages.yml을 참조하십시오.

강조 표시가 Markdown의 특정 언어에 대해 작동하지 않는 경우(즉, 언어가 지원되지 않음) https://support.magento.com/hc/en-us/에 게시할 때 적어도 강조 표시되게 하려면 다음 HTML을 사용하십시오.

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

여기서 ``%language-code%``은(는) [Prism.js 지원 언어](https://prismjs.com/#supported-languages)로 정의된 코드입니다.

## 목록

항상 빈 줄을 사용하여 목록과 나머지 컨텐츠를 구분합니다. 목록 앞과 뒤에는 빈 줄이 있어야 합니다.

순서가 지정된 목록에 대해 다음 형식을 사용하십시오.

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

순서가 없는 글머리 기호 목록을 만들려면 *, 또는 +, 또는 -로 줄을 시작합니다. 그러나 한 가지 방법을 선택하고 기사 전체에서 일관되게 사용하십시오.

예:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

목록 항목 사이에 내용을 추가하려면 줄의 시작 부분에 4개의 공백을 추가합니다.

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

이러한 방법으로 목록을 포함할 수도 있습니다.

## 링크

외부 링크는 간단합니다.

```markdown
[Adobe](https://www.adobe.com)
```

### 첨부 파일 링크

모든 종류의 첨부 파일은 .png, .jpg 및 .jpeg 형식이어야 합니다. 보안을 위해 다음 세 가지 형식 중 하나에 해당하는 첨부 파일만 허용합니다.

이미지를 삽입하려면 해당 문서와 동일한 섹션 폴더에 있는 *assets* 하위 폴더에 이미지를 넣고 다음 구문을 사용하여 이미지를 문서에 삽입합니다.

```markdown
![alt text](assets/image.png)
```

이미지 크기를 사용자 지정하려면 다음 HTML 태그를 사용하여 이 작업을 수행해야 합니다.

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### 문서의 특정 섹션에 대한 링크

문서 내의 섹션을 참조해야 하는 경우에는 별도의 앵커를 만들 필요가 없습니다. 모든 H2-H6 제목에 대해 게시 시 자동으로 생성됩니다. 앵커는 모든 단어를 소문자로 만들고 단어를 구분하는 &quot;-&quot;를 사용하여 헤더에서 생성됩니다.

예:

```markdown
## This is header
```

이 헤더에 대한 링크입니다.

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

헤더가 아닌 요소를 참조해야 하는 경우 HTML을 사용하여 추가할 요소를 정의하십시오. [id 특성](https://www.w3schools.com/html/html_id.asp)을 사용하십시오. 그런 다음 Markdown 또는 HTML 을 사용하여 이 ID를 참조할 수 있습니다.

### 상대 링크 및 기타 문서에 대한 링크

관련 링크를 사용하여 지원 기술 문서를 참조하지 마십시오. 문서가 [Adobe Commerce 도움말 센터](https://support.magento.com/hc/en-us)에 게시되면 해당 링크가 작동하지 않습니다.
[Adobe Commerce 도움말 센터](https://support.magento.com/hc/en-us)에서 전체 하이퍼링크를 사용하십시오.


## 표

테이블에 [HTML 서식을 사용합니다](https://www.w3schools.com/html/html_tables.asp).


## 경고 및 정보 블록

성공 참고 블록:

```
>![success]
>
>This is a success note
```

경고 블록:

```
>![warning]
>
>This is a warning
```

정보 메모 블록:

```
>![info]
>
>This is a block with additional info
```
