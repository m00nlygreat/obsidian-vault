# HTML

## 태그의 구조

- Opening Tag (여는 태그)
	- Tag name
	- Attiributes
		- key / value
		- 값이 없는 attribute도 있음.
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
- `<br/>` 태그: line-break
- `<hr/>` 태그: horizontal line
- `<a>` 태그: 하이퍼 링크
- `<ul>`, `<ol>` Unordered, Ordered List 태그
	- `<li>` 태그
- `<pre>`: pre-format

---

### 특수문자

HTML의 예약어로 사용되는 문자를 표시하는 방법

| 특수문자 | 설명                     |
| -------- | ------------------------ |
| `&nbsp;` | non-breaking space, 공백 |
| `&lt;`   | less than >              |
| `&gt;`   | greater than <           |
| `&quot;` | quotation mark "         |
| `&amp;`  | ampersand &              |

## 텍스트 서식

텍스트 안에서 사용되는 강조 등의 서식

- `<b>` 태그: bold
	- `<strong>`
- `<i>` 태그: italic
- `<u>` 태그: underline
- `<s>` 태그: strike-through
- `<sub>` 아래 첨자
- `<sup>` 윗첨자

---

### 기타 텍스트 서식

- `<ins>`, `<del>`: 문서에서 추가되거나 삭제된 등의 버전 관리를 하기 위해 표시
- `<em>`: emphasize 강조할 부분을 가리킴. 

## 테이블 태그
- 테이블 관련 태그는 표 형식의 데이터를 표시할 때만 쓴다.
- `rowspan`, `colspan` attribute를 사용해 셀 병합

```
<table>
	<thead>
		<th>열 제목</th>
		<th>열2 제목</th>
	</thead>
	<tbody>
		<tr> <!-- 행 태그 -->
			<th>내용 셀</th>
			<td>내용 셀2</td>
		</tr>
	</tbody>
</table>
```

## 정의 리스트

- `<dl>` description-list
- `<dt>` description-term
- `<dd>` description-description

### 주의사항

- `<dl>`은 반드시 하나 이상의 `<dt>-<dd>` 짝을 담고 있어야 합니다.
- `<dt>,<dd>` 는 `<dl>` 밖에서 독립적으로 사용할 수 없습니다.
- **단, `<dt>-<dd>`가 반드시 하나의 짝으로 지어져야 되는 것은 아닙니다.**  
    - 그래서 `<dt>`는 하나 이상의 `<dd>`를 형제 요소로 가질 수 있습니다. (예: `dt-dd-dd`)  
    - 그래서 하나 이상의 `<dt>`가 연속으로 나올 수 있습니다. (예: `dt-dt-dd`)
- `<div>`는 `<dt>-<dd>` 쌍을 감쌀 때 쓸 수 있지만, `<dt>-<dd>`의 형제 요소여서는 안 됩니다.
- `<dl>`은 공백이 아닌 텍스트 노드와 `<div>,<dt>,<dd>`가 아닌 요소를 포함해서는 안 됩니다.

## `<a>` 태그

- 자식 요소 또는 텍스트에 링크를 걸 때 사용 (anchor)

### attributes

- `href="{url}"`
- `target="_blank"`
- `download="{filename}"`

### 절대 / 상대 경로

- 절대경로: 최상위 경로 `/`에서부터 모든 경로를 입력
- 상대경로: 현재 경로 기준으로 상대적으로 경로를 찾아가기
	- `.` : 현재 디렉토리
	- `..` : 상위 디렉토리

## `<img>` 태그

웹 상에서 이미지를 표시하기 위한 태그

### attributes

- `src` : 이미지의 URI
- `width`, `height`: 너비, 높이 (생략 시 원본 크기)
- `alt`: 대체 텍스트

## `<form>` 태그

- 웹 서버와 통신하기 위한 유저 입력값을 받아 보관하고 전송처를 밝히는 요소
- 실제 화면상에 표시되는 것은 없으며, 오로지 `input` 요소의 값들을 취합하여 보내는 역할

### attributes

- `method`: `GET` 또는 `POST`
- `action`: 폼을 전송할 서버의 script 파일 지정 = URL
- 

## URL

## 시맨틱 태그

