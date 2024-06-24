# HTML

## 태그의 구성

- Opening Tag (여는 태그)
	- Tag name
	- Attiributes
		- key / value
		- 값이 없는 attribute도 있음.
- Content (내용)
- Closing Tag 

Closing Tag가 없고 Opening Tag만 있는 경우, 끝에 슬래시(`/`)를 붙여 표시해주기도 한다.


## HTML의 구성

`<!DOCTYPE html>`
이 문서가 HTML로 작성됐음을 밝히는 메타 태그

`<html>`
HTML 문서의 루트

`<head>`
문서의 내용이 아닌 메타 정보들을 기입하거나 스타일 시트, 자바스크립트 등을 연결한다.

`<body>`
문서의 내용에 해당하는 부분

`<!-- 주석 -->`
코드에 대한 설명

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

- [폼&인풋 한방정리](https://inpa.tistory.com/entry/HTML-%F0%9F%93%9A-%ED%8F%BCForm-%ED%83%9C%EA%B7%B8-%EC%A0%95%EB%A6%AC#%3Cform%3E_%ED%83%9C%EA%B7%B8)
- 웹 서버와 통신하기 위한 유저 입력값을 받아 보관하고 전송처를 밝히는 요소
- 실제 화면상에 표시되는 것은 없으며, 오로지 `input` 요소의 값들을 취합하여 보내는 역할

### attributes

- `method`: `GET` 또는 `POST`
- `action`: 폼을 전송할 서버의 script 파일 지정 = URL
- `name`: 스크립트에서 다루기 위한 이름, 식별자.

## `<input>` 태그

사용자의 입력을 받기위한 UI 엘리먼트

### attributes

- `type` : 인풋 요소의 형태를 결정
	- `text`, `tel`, `url`, `email`, `password`, `number`, `search`, `range`, `color`, `checkbox`, `radio`, `datetime`, `datetime-local`, `date`, `month`, `week`, `time`, `button`, `file`, `submit`, `image`, `reset`

## URL

Uniform Resource Locator. 어떠한 정보 또는 자원의 위치를 표현하기 위한 규격

```
프로토콜://사용자정보@호스트:포트/경로?쿼리#프래그먼트
```

## 컨테이너

- 별다른 기능이 없지만 다른 요소들을 감싸서 그루핑하고 사각형의 영역을 형성하는 태그
- `<div>` 태그: 블록 레벨 요소
- `<span>` 태그: 인라인 레벨 요소

### 시맨틱 태그 (Semantic Tags)

레이아웃에서 어떤 역할인지 밝히는 컨테이너 요소

- `<header>`, `<section>`, `<article>`, `<nav>`, `<aside>`, `<footer>`

![](attachments/Pasted%20image%2020240624163557.png)

# CSS

## Cascading Style Sheet

HTML 요소들을 꾸미는 방법을 정의하는 규칙

### Cascading (캐스케이딩, 계단식)

- 구체적으로 어떻게 계단식인가
	- 스타일 우선순위(Priority)
	- 스타일 상속(Inheritance)

## 스타일의 우선순위

1. 중요도
	- 작성자 > 사용자 > 사용자 도구
2. 명시도 (Specificity)
	- in-line > id > class > type
3. 코드 순서 (최신순)

## CSS 문법 구성

```
셀렉터 {프로퍼티 : 밸류; 프로퍼티2: 밸류 ... }
```

- 선택자(selector)와 선언부(declarations)로 구성
- 각 프로퍼티의 사이는 반드시 세미콜론(`;`)으로 구분

### `!important` Rule

- value의 뒤에 넣게 되면 즉시 최우선순위로 해당 스타일이 적용됨.

## CSS의 위치

- 외부 스타일(.css) 사용: 별도로 작성된 `css` 파일을 HTML에 연결하여 사용하는 방법. 비슷한 스타일을 여러 HTML 문서에 적용하고자 할 때 유리
- 내부 스타일: `<style>` 태그 안에 정의된 스타일 사용
- 인라인 스타일: 각 HTML 요소 안에 `style` attribute에 기술된 스타일
