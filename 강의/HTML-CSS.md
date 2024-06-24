## 태그의 구조

- Opening Tag (여는 태그)
	- Tag name
	- Attiributes
		- key / value
- Content (내용)
- Closing Tag 

Closing Tag가 없고 Opening Tag만 있는 경우, 끝에 슬래시(`/`)를 붙여 표시해주기도 한다.


## HTML의 구조

`<!DOCTYPE html>`
이 문서가 HTML로 작성됐음을 밝히는 메타 태그

`<html>`
HTML 문서의 루트

`<head>`
문서의 내용이 아닌 메타 정보들을 기입하거나 스타일 시트, 자바스크립트 등을 연결한다.

`<body>`
문서의 내용에 해당하는 부분

## `<head>`

### `<meta>`

메타 데이터를 표현하는 태그

#### 오픈 그래프(Open Graph)

```
<head>
  <meta property="og:title" content="웹페이지 제목" />
  <meta property="og:description" content="웹페이지 설명" />
  <meta property="og:image" content="웹페이지 이미지 URL" />
  <meta property="og:url" content="웹페이지 URL" />
</head>
```

웹사이트의 정보를 요약하고 대표하는 이미지를 표현하는 메타 태그

---

### `<title>`

웹사이트의 제목을 표시한다.

### `<link>`

사이트에 사용될 CSS 스타일시트, 자바스크립트 파일 등을 불러온다.

### `<style>`

문서 한정으로 정의된 CSS 스타일을 담을 수 있는 엘리먼트

### `<script>`

문서 한정으로 정의된 자바스크립트를 담아 불러올 수 있는 엘리먼트

## `<body>`

문서의 실질적인 내용을 담고 있는 파트

### 제목

- `<h1>` ~ `<h6>` 

### 본문

- `<p>` 태그: Paragraph
- `<a>` 태그: 하이퍼 링크
- `<ul>`, `<ol>` 태그
	- `<li>` 태그
- 