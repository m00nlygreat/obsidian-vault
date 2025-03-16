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

- **슬라이드 레이아웃 결정**:
    1. **comment_block**에서 `"key" == "layout"`인 항목을 찾으면, 해당 슬라이드에 `"layout"`을 강제 지정.
    2. 그렇지 않으면 자동 판단(또는 별도의 로직)에 따라 `"layout"` 부여.  
        예) `wildcard_break` 포함 시 `"two_columns"`, 이미지만 있으면 `"image_only"`, 텍스트+이미지 혼합이면 `"image_with_text"`, etc.

---

## **9. 예시: 종합 변환 사례**

### **9.1 입력(`md2json.py` 결과)**

```json
{
  "frontmatter": {
    "title": "My Document",
    "author": "Alice"
  },
  "tokens": [
    {
      "type": "heading",
      "attrs": { "level": 2 },
      "children": [{ "type": "text", "raw": "GPT 개요" }]
    },
    {
      "type": "comment_block",
      "key": "layout",
      "value": "cover"
    },
    {
      "type": "paragraph",
      "children": [{ "type": "text", "raw": "GPT는 자연어 처리 모델입니다." }]
    },
    {
      "type": "wildcard_break"
    },
    {
      "type": "paragraph",
      "children": [{ "type": "text", "raw": "이것은 새 placeholder에 들어갑니다." }]
    },
    {
      "type": "heading",
      "attrs": { "level": 2 },
      "children": [{ "type": "text", "raw": "다음 슬라이드" }]
    },
    {
      "type": "paragraph",
      "children": [
        { "type": "strong", "children": [{ "type": "text", "raw": "굵은" }] },
        { "type": "text", "raw": " 텍스트입니다." }
      ]
    }
  ]
}
```

### 9.2 최종 변환(`json2slide.py` 결과)

```json
{
  "slides": [
    {
      "title": "GPT 개요",
      "layout": "cover",
      "placeholders": [
        {
          "type": "text",
          "content": [
            {
              "runs": [
                { "text": "GPT는 자연어 처리 모델입니다." }
              ]
            }
          ]
        },
        {
          "type": "text",
          "content": [
            {
              "runs": [
                { "text": "이것은 새 placeholder에 들어갑니다." }
              ]
            }
          ]
        }
      ]
    },
    {
      "title": "다음 슬라이드",
      "layout": "title_content",
      "placeholders": [
        {
          "type": "text",
          "content": [
            {
              "runs": [
                { "text": "굵은", "bold": true },
                { "text": " 텍스트입니다." }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

- 첫 번째 슬라이드: `comment_block`(`layout: cover`)에 따라 **`layout`이 `"cover"`**로 지정.
- `wildcard_break`로 인해 **placeholders**가 2개 존재.
- 두 번째 슬라이드: **새로운 H2**로 인해 슬라이드 생성, **layout**은 `"title_content"`(자동 판단).

---

## **10. 구현 시 주의사항**

1. **빈 슬라이드** 방지
    
    - 슬라이드가 시작되었는데 콘텐츠가 하나도 없는 경우는 무시하거나 조정.
2. **빈 placeholder** 방지
    
    - `wildcard_break`가 연속으로 나와 placeholder가 생성되었으나 내용이 없는 경우는 무시할 수 있음.
3. **들여쓰기 리스트(depth)**, **코드 블록**, **인용문(quote)** 등 세부적인 토큰 변환
    
    - 모든 텍스트는 결국 `runs` 형태로 변환하여 스타일(bold, italic, monospace 등)을 설정.
4. **이미지, 표, 차트는 python-pptx 함수**로 변환 시 주의
    
    - `add_picture`, `add_table`, `add_chart` 등.
    - JSON 구조에서는 `type: "image"`, `type: "table"`, `type: "chart"` 등의 형식으로 구분.
5. **comment_block**의 다른 `key`가 나올 수도 있음
    
    - 예: `[notes]: # (Slide note...)` → 슬라이드 노트에 활용 가능.
6. **title과 0번 placeholder**
    
    - 실제 PPT 변환 시 `title`을 0번 placeholder로 매핑해도 되고,  
        JSON 상에서는 가독성을 위해 **`title` 필드를 분리**해두는 것을 권장.

---

# **맺음말**

이 백서는 **마크다운에서 JSON**을 거쳐 **PPT**로 변환하기 위해 필요한 **json2slide.py** 규칙을 총망라했습니다.

- **슬라이드 구분** (H2, thematic_break)
- **placeholder 구분** (wildcard_break)
- **텍스트 스타일** (run 단위)
- **이미지, 표, 차트 등 비텍스트 요소** 처리
- **comment_block**을 통한 layout 강제 지정

이 규칙을 기반으로 구현하면,  
**markdown → md2json.py → (중간 JSON) → json2slide.py → (슬라이드 JSON) → python-pptx → PPT**  
라는 파이프라인이 보다 안정적으로 동작하게 될 것입니다.

추가적인 세부 사항(예: 컬러, 폰트 크기, 레이아웃 템플릿 등)은 **python-pptx** 구현 단계에서 자유롭게 커스터마이징할 수 있습니다.

이상으로 **json2slide.py** 변환 규칙 백서를 마치겠습니다.