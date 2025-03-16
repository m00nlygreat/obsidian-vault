# **백서: json2slide 변환 규칙**

## **1. 개요**

- **md2json.py**는 마크다운 파일을 분석해 YAML frontmatter와 본문을 파싱하여,  
    **frontmatter**와 **tokens** 구조를 갖춘 JSON을 출력합니다.
- **json2slide.py**는 **md2json.py**의 출력을 받아, **슬라이드(및 placeholder) 구조를 갖춘 JSON**으로 재구성합니다.
    - 최종적으로 이 JSON은 **python-pptx**를 이용해 PPT 파일을 생성할 때 사용합니다.

## **2. 데이터 흐름**

1. **Markdown 파일** → (md2json.py) → **1차 JSON**  
    (마크다운 토큰들이 담긴 JSON: frontmatter + tokens)
    
2. **1차 JSON** → (json2slide.py) → **2차 JSON**  
    (슬라이드 및 placeholder 구조로 가공된 JSON)
    
3. **2차 JSON** → (python-pptx) → **PPT 파일**  
    (실제로 PowerPoint 문서를 생성)
    

---

## **3. md2json.py가 제공하는 JSON 예시**

```json
{
  "frontmatter": {
    "title": "My Document",
    "author": "Alice",
    "date": "2025-03-16"
  },
  "tokens": [
    {
      "type": "heading",
      "attrs": { "level": 2 },
      "children": [
        { "type": "text", "raw": "GPT 개요" }
      ]
    },
    {
      "type": "paragraph",
      "children": [
        { "type": "text", "raw": "GPT는 자연어 처리 모델입니다." }
      ]
    },
    {
      "type": "wildcard_break"
    },
    ...
  ]
}
```

### **3.1 frontmatter**

- 문서의 메타정보를 포함 (title, author, date 등).

### **3.2 tokens**

- 본문을 마크다운 단위별로 토큰화한 리스트.
- 주요 **type**:
    - **heading**: `level`로 H1~H6 구분.
    - **paragraph**: 일반 텍스트 단락.
    - **list**: 순서 있는/없는 목록.
    - **wildcard_break**: 슬라이드 내 컬럼(placeholder) 구분 용도.
    - **thematic_break**: 슬라이드 구분 용도(또는 필요에 따라 다른 해석 가능).
    - **comment_block**: 주석(`key`, `value` 쌍). 주로 layout 정보를 강제 지정하기 위해 사용.
    - **image**: 이미지 삽입용.
    - **quote**: 인용문.
    - **code**: 코드 블록.
    - **table**: 표.
    - ...

---

## **4. json2slide.py의 출력 구조 (최종 JSON)**

### **4.1 슬라이드 구조**

```json
{
  "slides": [
    {
      "title": "슬라이드 제목",
      "layout": "title_content",
      "placeholders": [
        {
          "type": "text",
          "content": [
            {
              "runs": [
                { "text": "이것은 일반 텍스트입니다." },
                { "text": "굵게", "bold": true },
                { "text": " 표시된 텍스트입니다." }
              ]
            }
          ]
        },
        {
          "type": "image",
          "src": "attachments/example.png"
        }
      ]
    },
    ...
  ]
}

```

#### **슬라이드 객체의 주요 필드**

1. **title**: 슬라이드 제목
    - 실제 PPT 변환 시 **placeholder[0]**로 매핑될 수 있음.
2. **layout**: 슬라이드 레이아웃(예: `"title_content"`, `"two_columns"`, `"cover"`, 등)
    - **comment_block**에서 `layout`이 지정된 경우 우선 적용.
    - 지정이 없으면 자동 판단 가능.
3. **placeholders**: 슬라이드 내 콘텐츠를 담는 ‘구획’들
    - `wildcard_break`를 만나면 **새로운 placeholder** 생성.
    - placeholder 배열 안에 **텍스트, 이미지, 테이블, 차트 등**이 들어갈 수 있음.

---

### **4.2 Placeholder 구조**

```json
{
  "type": "text",
  "content": [
    {
      "runs": [
        { "text": "Hello" },
        { "text": "World", "italic": true }
      ]
    }
  ]
}
```

혹은

```json
{
  "type": "image",
  "src": "attachments/example.png"
}
```

혹은

```json
{
  "type": "table",
  "rows": [
    ["헤더1", "헤더2"],
    ["데이터1", "데이터2"]
  ]
}
```

#### **placeholder**의 주요 속성

1. **type**
    - `"text"`: 일반 텍스트나 리스트 등을 모두 합쳐 텍스트로 취급.
    - `"image"`: 이미지.
    - `"table"`: 표.
    - `"code"`: 코드 블록.
    - `"quote"`: 인용문.
    - `"chart"`: (차트가 있을 경우)
    - `"list"`: 리스트를 별도 type으로 둘 수도 있음(혹은 `"text"` 내 runs로 처리).
2. **content** (혹은 `rows`, `src` 등)
    - `"text"`인 경우: `content` 안에 run 단위 텍스트.
    - `"image"`인 경우: `src`로 이미지 경로.
    - `"table"`인 경우: `rows`로 2차원 배열.
    - `"code"`인 경우: `monospace: true`와 함께 텍스트 runs를 처리.

---

## **5. 텍스트 스타일(run) 구조**

**python-pptx**에서 텍스트 스타일은 **run 단위**로 적용하므로,  
JSON에서도 **run 단위**로 스타일을 지정한다.

|속성|의미|
|---|---|
|`bold`|`true`면 굵게 표시 (굵은 글꼴)|
|`italic`|`true`면 이탤릭(기울임꼴) 적용|
|`underline`|`true`면 밑줄|
|`monospace`|`true`면 고정폭 글꼴 (코드 블록 등)|
|`text`|실제 텍스트 내용|
|`hyperlink`|`{"address": "http://..."} 등`으로 하이퍼링크 표시 가능|

예시:

```json
"runs": [
  { "text": "이것은 " },
  { "text": "강조된", "bold": true },
  { "text": " 텍스트입니다.", "italic": true, "hyperlink": { "address": "http://example.com" } }
]
```

---

## **6. 슬라이드 분리 규칙**

1. **`heading level 2 (H2)`**: 새로운 슬라이드 시작
2. **`thematic_break`** (`---` / `___`) (옵션) : 새로운 슬라이드 시작
3. **`heading level 1 (H1)`**: 간지(섹션 표지)로서 독립 슬라이드 (필요 시)

이 부분은 프로젝트 요구사항에 따라 달라질 수 있음.  
예) H2가 아닌 H1로 분리하거나, `wildcard_break`로 슬라이드 구분할 수도 있음.

---

## **7. placeholder 분리 규칙 (`wildcard_break`)**

- **`wildcard_break`** (`***` 등)가 등장하면, **현재 슬라이드 내에서 새로운 placeholder**를 생성.
- 즉, 한 슬라이드 안에서 구획을 나눌 때 사용. (예: 두-세 개의 컬럼, 혹은 다른 섹션 등)
- 텍스트, 이미지, 테이블 등 서로 다른 유형의 콘텐츠를 나눌 수도 있고, 필요하면 하나의 placeholder에 여러 텍스트 블록을 모을 수도 있음.

---

## **8. `comment_block`와 layout 지정**

- **`comment_block`** 형태:

```json
{
  "type": "comment_block",
  "key": "layout",
  "value": "custom_layout",
  "raw": "[layout]: # (custom_layout)"
}
```

