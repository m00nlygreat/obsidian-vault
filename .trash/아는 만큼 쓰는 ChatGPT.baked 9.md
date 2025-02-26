---
title: 아는 만큼 쓰는 ChatGPT
author:
	- 배문형
---

# 들어가며

## ChatGPT 강의는 이제 안 하고 싶은데요...

### ChatGPT에 대한 푸념

- 원리도 이론도 필요없다
- 생각만큼 그렇게 대단한 건 아니고
- 예제가 에상대로 잘 안돼요
- 가끔 그냥 안 됨
- 불현듯 업데이트되어 바뀜

## ChatGPT와 생성형 AI에 대한 오해

- “대박 쉬운 ChatGPT로 코딩하기” -> 안 쉬움
- "해외에서 난리난 ChatGPT 신기능” -> 난리 안남
- 90% 이상의 생성형 AI 관련 지식들은 유튜브를 통해 유통되고, 전파됨
- 계속해서 새로운 것이 나오는 특성상 어느 시점에서 마스터했다라는 것은 있을 수 없음.

## 그럼 어떻게 공부할까

- 형식지와 암묵지, explicit and tacit knowledge
- 흥미본위의 유튜브 탐색과 당장의 업무 활용으로
- 폭넓게 바라보고 여러 맥락 안에서 AI를 이해하기

![](attachments/image33.png)

---

## S.T.A.R 프레임워크

- [경희대 김상균 교수의 AI 학습/훈련법](https://www.youtube.com/watch?v=sDBDHF6m578)
	1. 시간이 가장 많이 투입되는 일 찾기
	2. 개선하고 싶은 나의 핵심 역량
	3. 하고싶은데 못해본 것 찾기
	4. 시간이 더 많이 있으면 해보고 싶은 것

- 더 전문성이 있는 사람이 AI를 활용했을 때 차별화를 가져올 수 있다.
	- 일자리 -> 일거리: 전통적 직업의 해체
	- 직업 -> 스킬:  

![](attachments/Pasted%20image%2020240726085235.png)

## ChatGPT

- OpenAI 가 발표한 Generative Pre-trained Transformer 모델의 생성형 AI
- Transformer: 2017년 구글. 단어들 간의 유사도를 찾아내서 (셀프 어텐션) 의미를 알아서 학습하는 모델. 

### 생성형 AI (Generative AI)

- 완성된 그림, 음악, 글 등을 작은 조각으로 나누어서 가지고 있는 거대한 레고블럭 박스

![](attachments/file-mqBlhyrMG4ynB1uCWsFq5m3r.png)

---

### 대규모 언어모델 (Large Language Models, LLM)

- 인터넷 등에 쓰여진 대량의 텍스트를 학습하여 
- 주어진 글의 다음에 올 확률이 높은 단어를 배치하는 인공지능 모델
- 개발자들도 원리를 잘 모른다!
	- ChatGPT 자신도 스스로 무슨 말을 하는지 모름!
	- [앤스로픽, AI블랙박스 작동원리 밝혀냈다...“칭찬하면 오만해져”](https://www.mk.co.kr/news/it/11021534)

![](attachments/image7.png)

---

![](attachments/1678583134640d255e2f927.png)

---

### 멀티 모달

- 텍스트만이 아니라, 이미지, 비디오, 음악 등을 입력받아 동시에 처리하는 AI
- GPT-3.5 는 불가하고, GPT-4는 가능한 것
- 구글 Gemini는 바닥부터 멀티 모달을 기반으로 만들어짐
- GPT-4o 의 멀티모달

![](attachments/image1.png)

---

## 환각 (Hallucination)

- 세종대왕 맥북 던짐 사건

### RAG (Retrieval-Augmented Generation)

- 범용으로 제작된 LLM에 특정 목적의 데이터를 첨부하여 정확하고 전문성 있는 답변을 생성하는 기술

![](attachments/Fpdln-jaMAA-Gw1.jpg)

# AI 이모저모

## AI의 역사

### 인공지능 (Artificial Inteligence)의 두 갈래

- 알고리즘 기반 (Rule-based Systems)
	- 사람이 모든 규칙과 조건을 제시하여 그대로 수행하는 인공지능
	- 사람이 지시한 것 이외에는 할 수 없음
- 인공신경망 기반 (Machine Learning)
	- 뉴런을 모방하여 인간 두뇌와 비슷하게 작동하는 인공 신경망 (Neural network)
	- 막대한 연산량 필요

---

![](attachments/Neuron.png)

---

![](attachments/nnet2.png)

---

::: notes

### 알고리즘과 신경망의 대결

- 1950년대, 인공지능에 대한 구상 중 인공 신경망 개념 등장
	- 도형을 인식하는 퍼셉트론 (Perceptron)
- 2010년초 제프리 힌턴에 의해 재발견됨.
	- 심층 인공신경망(Deep Neural network)과 딥 러닝의 발견
	- 이미지 인식 경연대회에서 놀라운 성과
	- 딥마인드와 알파고의 등장
	- OpenAI와 ChatGPT의 등장
:::

![](attachments/image9.png)

## LLM의 종류

![](attachments/image2.png)

## 오픈 AI와 일론 머스크

![](attachments/image31.png)

::: notes

- AI에 대해 상반된 두 가지 입장
	- AI는 위험하며 투명하게 공개되고 통제되어야 함 (허사비스, 머스크)
	- AI는 인류의 발전을 가져올 중요한 파트너 (페이지)
- 일론 머스크, AI 발전을 감시하기 위해 딥마인드 지분 구입

### 딥마인드 구글에 인수

- 머스크 반발

:::

---

### 머스크 오픈AI 설립

- 일론, 샘 올트먼, 일리야 수츠케버 등
- 오픈AI와 테슬라 병합 시도
- 실패 후 마이크로소프트에 지분 전량 매도

### 오픈AI의 대성공

- 오픈AI, CEO 샘 올트먼 해임 및 복직
- 머스크 x.ai 설립
- 샘 올트먼, 초정렬팀 해체
	- 일리야 수츠케버 퇴사

 ![](attachments/image5.png)

## AI의 미래

### 강 인공지능 (Strong AI)

- 약 인공지능 (Weak AI)
	- 특정한 분야의 일을 인간의 지시에 따라 수행하는 인공지능
- 스스로를 업데이트하는 인공지능 (AGI, 일반 인공지능)

### AI와 인간의 가치

- 로마시대 콜로세움의 이야기
- Genuine, authentic한 인간에의 선호

![](attachments/image32.png)

## AI 이모저모

### 승리의 키

- 하드웨어 vs 소프트웨어?
	- H100, H200, B200 .. 
		- NVIDIA, AI Saas 
	- NVIDIA의 승리는 어디까지인가
		- 인텔, 메타, Groq 등 빅테크 들의 탈NVIDIA를 위한 노력
		- [짐 켈러 "엔비디아 시대는 결국 끝난다.."](https://www.youtube.com/watch?v=2pw-YZ7KuFY)
	- Sora와 대항마들
		- Sora
		- Vidu, Kling
		- Luma Dream Machine

---

- Data 보유
	- 빠르면 2025년 학습시킬 데이터 고갈
	- AGI 달성을 위한 키

- 온디바이스 AI
	- 갤럭시?
	- 개인화의 측면, 비용의 측면
- OpenAI, 동영상 생성 AI Sora 발표
	- 중국판 Sora, Vidu와 Kling

---

### GPT-4o

- GPT-4 Omni
	- 진정한 멀티 모달
	- `im-a-good-gpt2-chatbot`과 `also-a-good-gpt2-chatbot`
- 1/2 정도의 토큰을 쓰고도 같은 성능
	- 무료 사용자에게도 제공
	- GPTs 무료화
- [Say Hello to GPT-4o](https://www.youtube.com/watch?v=vgYi3Wr7v_g)
- [Be My Eyes Accessibility](https://www.youtube.com/watch?v=KwNUJ69RbwY)

![](attachments/Pasted%20image%2020240614023735.png)

---

### 2024 애플 WWDC

- 애플 인텔리전스
	- 10 TOPS, 1.5GB 의 성능으로 온디바이스로 작동
- AI 에이전트: 시스템과의 Integration
	- 애플 2024 WWDC, Siri와 ChatGPT의 통합

![](attachments/Pasted%20image%2020240609231252.png)

# ChatGPT 사용해보기

## 소개

![](attachments/image6.png)

## 질문해보기

### 간단한 의견 물어보기

- 검색엔진을 대신하는 GPT의 사용법
- 질문해볼 만한 내용들
	1. "아인슈타인의 상대성 이론에 대해 초등학생도 이해할 수 있도록 쉽게 설명해줘."
	3. "네가 세계종말을 원하는 슈퍼 빌런이라면, 세계 멸망을 위해 무엇을 하겠어?"

![](attachments/image3.png)

---

### 맥락을 유지한 채 계속 질문하기

- 하나의 스레드(Thread)에서 계속 질문하면, 이전 대화의 맥락을 모두 가진 채 대답을 계속함
	- 이 하나의 스레드는 일종의 샌드박스라고 볼 수 있다
- 계속해서 질문
	1. "그게 당시의 과학계에 어떻게 받아들여졌고 어떤 시사점을 가져왔어?"
	2. "너의 슈퍼빌런 특성은 모든 대사에 블랙유머를 넣어 말하는 거야. 네가 말하는 모든 것들은 세계를 구하기 위해서라고 하지만 실제로는 세상을 멸망시키는 것이거든. 네가 할 법한 대사를 말해볼래?"
- 회신하기(Reply)

![](attachments/Pasted%20image%2020240323133617.png)

---

### 계속 생성하기

- 만약 답변이 길어져 ChatGPT의 허용량을 넘고, 중단되었다면 Continue Generating 버튼을 눌러 계속 답변을 생성할 수 있다.

### 답변 재생성하기 

- ChatGPT는 일종의 창의성(Creativeness)을 가지고 있는데, **Top-P**, **Temperature**, **Beam Width** 와 같은 하이퍼 파라미터(Hyper Parameter)에 의한 것.
- 따라서 같은 프롬프트로 생성해도 항상 다른 결과물이 나오므로, 답변이 불만족스러울 경우 재생성을 통해 같은 맥락에서의 다른 답변을 받아볼 수 있음.

![](attachments/image11.png)

# 프롬프트 엔지니어링

## 프롬프트 잘 쓰기

- 프롬프팅을 잘하는 것은 **대화를 잘하는 것**

### 대화를 잘 한다. 라는 것

- 상대방의 의도를 이해하고, 나의 의도를 오해없이 전달하는 것
	- '경청'의 중요성
- 맥락과 의도를 설명하는 충실함.
- 내가 당연히 알고 있는 것들에서 벗어나 상대가 파악한 수준을 고려하기
- 즉 대화를 잘 한다는 것은 '태도의 문제'라고 볼 수 있음.

![](attachments/Pasted%20image%2020240323140231.png)

---

### 프롬프트의 필수 요소들

- **Task** 무엇을 해야하는지
- **Context** 어떤 상황인지
- **Persona** 어떤 역할이 되어야 하는지
- **Example** 예시로는 어떤 것이 있는지
- **Format** 어떤 형태로 작성해야 하는지
- **Tone** 어떤 어조를 사용할 것인지

![](attachments/image8.png)

---

#### Before

- "상온 상압 초전도 물질 LK-99의 실패를 보고하는 보고서를 작성해줘"

***

#### After

- "상온 상압 초전도 물질 LK-99의 개발 실패를 보고하는 보고서를 작성해줘. 너는 세계 최첨단 수준의 연구를 진행하는 연구소의 가장 유능한 시니어 연구원으로서 LK-99의 실패에 대한 보고서를 작성해줘야해. LK-99는 실패했지만 우리 연구소에 지원되는 자금에 영향은 없어야 하므로 앞으로의 연구를 계속해야 한다는 뉘앙스를 띠어야해. 물론 그러한 의도는 숨겨야 하고. 예를 들면 다음 번 연구에서는 어떤 물질을 더 첨가해서 초전도성을 띠도록 유도할 수 있을지도 모른다는 예측을 추가해서 설득력을 높일 수 있어. 답변은 요약, 도입, 배경, 실패의 원인, 기술적 필요사항, 앞으로의 로드맵, 결론 등의 항목을 중심으로 전문용어를 섞어 전문가처럼 보이도록 설명해주면 좋겠어."
- [LK-99 보고서](https://chat.openai.com/share/ff2be24f-2f7e-4f65-91ad-6a3386de3106)

---

### 스무고개형으로 질문하기

- 대화 중심으로 프롬프팅을 완성해가는 방법
- 맥락을 바꿔버리거나 너무 일관성 없는 대화를 하나의 스레드에서 다루지 않도록 주의
- 잘못된 답변 역시 입력으로 다시 들어가기에, 잘못된 답변을 놔두고 계속 맥락을 이어가면 안 됨.
- [티켓의 가치](https://chat.openai.com/share/cde241e6-3087-40d0-b31b-6deb3e53891f)

- 사내 의사결정을 위한 보고서 작성
	- 고향만두라는 이름의 냉동 만두를 만드는 회사에서 일하고 있어, 고향만두는 오랫동안 사람들에게 사랑받아왔고 최근 점보 육개장, 점보 크림빵과 같은 유행에 발맞추어 점보 고향만두를 출시하려는 계획을 가지고 있어. 점보 고향만두를 출시해야한다고 이사회를 설득하기 위한 주장과 근거를 만들어줘

![](attachments/Pasted%20image%2020240323150341.png)

---

### '가스라이팅'

- 협박하기
- 도발하기
- 강조하기
- 애원하기
- 보상하기/벌하기
- '미안하지만...' 금지


![](attachments/Pasted%20image%2020240323171759.png)

---

### few-shot

- 예시를 밝혀 답변의 구조 또는 여러 측면을 제한하는 방법
- [일정 묻기](https://chat.openai.com/share/a74f8ea7-9f7a-43f0-8bdc-4dbfb86cd3ba)


![](attachments/image4.png)

---

### chain-of-thought

- 연쇄적 사고. 단계를 풀어헤쳐 자연스럽게 답을 유도하기
	- step by step

![](attachments/Pasted%20image%2020240324023859.png)

---

### '해줘'

- 목적을 제시하고, 이를 위한 정보를 GPT가 사용자에게 질문하게 하여 맥락을 채워나가는 방법
	- "다음 두 개 프로젝트 중 하나를 골라서 다음 주 임원 회의에 기획안을 제출해야 해. 둘 중 하나를 선택하는 데에 도움을 줄래? 필요한 것들을 나에게 물어봐 줘"
		1. 이벤트성 점보 고향만두 냉동식품 출시
		2. [첵스나라 대통령 선거](https://namu.wiki/w/%ED%8C%8C%EB%A7%9B%20%EC%B2%B5%EC%8A%A4%20%EC%82%AC%EA%B1%B4#s-3.2)
	- [프로젝트 선택 도움](https://chat.openai.com/share/614216da-4661-4eae-9518-c6cb5140e80f)
- 우리가 처음 언어를 배울 때 자신의 필요만을 얘기하는 것처럼. 주도권 자체를 GPT에게 줘버리기
- "이 결과가 맘에 들어. 다음에 다른 텍스트로도 동일한 결과를 낼 수 있도록 너에게 보낼 프롬프트를 작성해줘"
- [프롬프트 엔지니어 회의론 증가](https://www.aitimes.com/news/articleView.html?idxno=158070)

---

![](attachments/image12.png)

## 마크다운(Markdown)

- HTML의 Subset인, 리치 텍스트를 표현하기 위한 간이 문법
- 이름부터 HTML(Hypertext Markup Language)의 오마주

### 플레인 텍스트와 리치 텍스트

- 플레인 텍스트: 메모장
- 리치 텍스트: 워드패드

### 사용처

- 디스코드, 슬랙, 노션
- Obsidian, LogSeq, Github
- ChatGPT, StackEdit

![](attachments/Pasted%20image%2020240610005835.png)

## 마크다운의 문법 소개

1. **제목**: `# 제목`, `## 작은 제목`, `### 더 작은 제목`
2. **텍스트**:
    - **굵게**: `**텍스트**`
    - *이탤릭*: `*텍스트*`
    - ~~취소선~~: `~~텍스트~~`
3. **인용문**: `> 인용문`
4. **리스트**:
    - 순서 있는 리스트: `1. 항목`
    - 순서 없는 리스트: `- 항목`
5. **코드**:
    - 인라인 코드: `` `코드` ``
    - 블록 코드: 
    ````
    ```
    코드 블록
    ```
    ````

---

6. **링크**: `[링크 텍스트](URL)`
7. **이미지**: `![대체 텍스트](URL)`
8. **수평선**: `---`
9. **테이블**:
    | 헤더1 | 헤더2 |
    |-------|-------|
    | 셀1   | 셀2   |
10. **체크박스**:
    - `[x] 완료 항목`
    - `[ ] 미완료 항목`


# ChatGPT 고급 기능 소개

## Custom Instruction

- ChatGPT가 좀 더 사용자 친화적으로 대답할 수 있도록 사용자의 정보나 답변에 있어서의 희망사항을 미리 알려주기

![](attachments/image34.png)

## Vision & DALL-E

::: notes
- GPT-4 Vision: 사진을 보고 해석하는 능력
	- 프롬프트에 사진 파일을 첨부
- DALL-E 3: 프롬프트 기반으로 이미지를 생성하는 능력 (Midjourney와 같은)
	- '그림을 그려줘.', '이미지를 생성해줘.' 등의 표현 사용
- 풍경 사진, 이미지에서 도표, 이미지로 된 텍스트까지
:::

![](attachments/image10.png)

## Browsing

- 실시간으로 인터넷을 검색하고, 검색한 내용을 기반으로 추론, 분석하는 것
	- '최근', '오늘', '2024년' 등 시점을 가리키는 표현
	- LK-99 등 최근 화제가 되었던 연속성 있는 이슈
	- '검색해줘' 등의 직접적인 표현
- 기존 ChatGPT의 데이터 학습 시점
	- GPT-3.5: 2022년 1월 까지
	- GPT-4: 2023년 12월 까지
	- GPT-4o: 2023년 9월 까지

![](attachments/image13.png)

## Data Analysis

- 파이썬 백엔드를 실행하여 데이터 분석 등을 수행하는 기능
	- 파일 리딩: CSV, PDF, PPT, XLS, DOC 등 문서 제공
	- '차트를 그려줘.'와 같은 표현
- 알아서 파이썬 코드를 짜고 실행함.
	- 오류 발생 시 자동으로 재시도
- 기본적으로 파이썬으로 수행가능한 데이터 분석, 파일 관련, 수학 등의 요청을 받아들이나, API콜, 크롤링 등 시스템에 영향을 주거나 부담스러운 작업은 거절
	- [ChatGPT로 동영상 만들기](https://www.clien.net/service/board/lecture/18553432)

![](attachments/image14.png)

## GPTs

- 자주 사용하는 GPT 프롬프트 설정을 별도의 GPT로 만들어서 편리하게 독립된 채널에서 대화하기
- GPT-4의 모든 기능 사용 가능: Vision, Browsing, Data Analysis
- 액션: 요청 받은 텍스트의 내용에 따라, 외부 API를 사용해서 전용 기능을 실행하고 그 응답결과를 답변 처리에 사용가능
- 만든 GPT는 스토어에 올려 누구나 쓸 수 있게 만들거나, 유료화할 수도 있음

![](attachments/image15.png)

## ChatGPT App Mobile/Mac

- 설치형ChatGPT 앱
- ChatGPT와 음성대화 가능!
- 백그라운드 대화

![](attachments/image35.png)

# 실전 ChatGPT

## 경위서 쓰기

- [제가 왜 늦었냐면요 - 티키틱](https://www.youtube.com/watch?v=aODhSiEI9qM)
- [제가 왜 늦었냐면요](https://chat.openai.com/share/cdd255b5-7c0a-47a9-8cfa-c350cad1106e)
	- 지각에 대해 사죄하는 경위서
	- 공손하고 정중하게 상황을 설명
	- 다음부터 늦지 않을 것임을 강조
- 경위서를 워드(docx)파일로 내보내기

![](attachments/image16.png)

## 이력서를 주고 물어보기

- PDF, PPT, XLS, DOC, TXT, MD 등 다양한 포맷의 파일을 제공하고 내용에 대해 질문하거나, 내용을 기반으로 추론하거나, 데이터 분석 등을 의뢰
- 이력서를 제공하고 아래와 같은 것들 [물어보기](https://chat.openai.com/share/73b5a668-452b-4645-a351-f76d5a22effb)
	- 현재 회사 내에 문제들을 해결하는 데에 도움을 줄 수 있는 사람일지?
	- 우리 팀에 들어왔을 때 문제가 될 수 있을만한 가능성?
- [채용 후보 관리 엑셀 파일을 작성](https://chat.openai.com/share/3ece436c-e7d3-4123-8974-5a2bd4af6caf)하고, 후보자를 추가시키기

![](attachments/image17.png)

## 회사의 재무제표 분석

- 재무제표 데이터를 주고, [이것저것 물어보기](https://chat.openai.com/share/1439534a-edf4-46ff-adf1-195e31b81ba2)
	- 이 회사의 성과가 증가한 이유?
	- 앞으로 어떤 점을 중점으로 운영해나가면 좋겠는지?
	- 한국의 현 상황과 관련하여 투자의견 제안
- 재무제표 분석 결과, 투자 관련 의견을 작성하여 보고하기

![](attachments/image18.png)

## 아보카도 가격 분석

- [캐글 - 아보카도 가격 분석](https://www.kaggle.com/datasets/neuromusic/avocado-prices)
- 미국의 일별 / 지역별로 기록된 아보카도 평균 가격과 판매량 데이터를 주고 [물어보기](https://chat.openai.com/share/f2bf4f19-2995-4cbf-9415-0e83df2287c4)
	- 같은 기간 동안 가장 많이 오른 지역은?
	- 아보카도 가격에 가장 많이 영향을 주는 요소는?

![](attachments/image19.png)

## 스포티파이 곡 재생 데이터 분석

- [캐글 - Most streamed spotify songs 2023](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023)
- 2023년의 스포티파이 곡 재생 데이터를 주고 [물어보기](https://chat.openai.com/share/38c1cee9-a476-4381-897f-ba107ee8b791)
	- 얼마나 많은 K-Pop 곡들이 순위에 올라왔나?
	- 2023년의 전체적인 무드는?
	- 스포티파이에 진출한 K팝 아티스트들의 비중을 파이차트로 그리기

![](attachments/image20.png)

## GPTs

- PDF로 된 신입사원 매뉴얼을 학습하고, 신입사원의 질문에 답하는 GPT 만들기
	- 친절한 말투를 사용하고 긍정적인 답변을 해야함 (Tone, Attitude)
	- 신입사원 매뉴얼에 없는 내용, 곤란한 내용은 인사팀장에게 안내
	- [친절한 김대리](https://chat.openai.com/g/g-bEYIII6S6-cinjeolhan-gimdaeri)

![](attachments/image22.png)

## 원영적사고 GPT 만들기

- [원본](https://getgpt.app/play/1drEpYwXhT?list=d9926747-7a55-4b38-a80d-2982de281d5f)
- 어떤 Instruction을 주었을까? 생각해보기
- [까칠한 그녀 GPT](https://chatgpt.com/g/g-wIpN0ihcQ-ggacilhan-geunyeo)

![](attachments/Pasted%20image%2020240610015849.png)

## 텍스트를 파워포인트 슬라이드로 만들기

- 줄글을 알맞게 슬라이드로 구분하기
- 테마 적용해서 디자인 완성하기
- [슬라이드 만들기](https://chat.openai.com/share/32212d7c-c30a-45ff-bf3e-fe0b39b0c2ff)

![](attachments/image23.png)

## 엑셀에서 ChatGPT 활용하기

### 샘플 데이터 만들어주기

- 엑셀에서 사용하기 위한 샘플 데이터를 생성
- 테이블 형태로 반환된 [데이터](https://chat.openai.com/share/cca1a314-d09f-4ec5-8aac-aca52131b16a)는 엑셀, 구글 시트 등에 붙여넣어서 사용

![](attachments/image24.png)

---

### 함수 대신 만들어주기

- 함수를 텍스트로 설명하면 대신 생성
- 파라미터로 제공되어야 하는 데이터의 위치와 형식을 설명할 필요 있음
 
![](attachments/image25.png)

## GPT를 엑셀 안에서 사용하기

- ChatGPT API를 사용하여 엑셀 안에서 함수를 통해 GPT를 사용하게끔 도와주는 추가기능
- [gptforwork.com](https://gptforwork.com)

![](attachments/image26.png)

---

### 기존 데이터와 연관된 데이터 생성하기

- 회원의 이름, 나이, 직업을 고려하여 선물 제안하기
- `GPT(프롬프트, [참조값], [온도])` 함수 사용하기
 
![](attachments/image27.png)

---

### 알맞은 해시태그 달기

- 여행코스에서 여행지와 체험하는 문화를 꺼내어서 해시태그 형태로 표현.

![](attachments/image28.png)

---

### 내용 분류하기

- 정성적인 평가를 긍정과 부정의 뉘앙스, 그리고 긍정 부정의 정도를 평가하기.
- `GPT_LIST("프롬프트", [참조값], [온도])` 함수 사용하기

![](attachments/image29.png)

---

### 패턴 파악해서 채우기

- Before와 After의 결과값 예시를 주고 다량의 Before 값을 After 형식으로 변환하기
- `GPT_FILL(패턴 범위, 입력 범위, [온도])` 함수 사용하기

![](attachments/image30.png)

## VBA

- Visual Basic for Applications
- 초보자를 위한 베이직

### 매크로

- 엑셀의 작업이나 다른 프로그램 처리를 로직을 통해 자동화

### 사용자 함수

- 기존 엑셀 함수에 더해 사용할 수 있는 사용자 커스텀 함수를 VBA로 제작

## 근태 체크 엑셀 매크로 만들기

- 출근/퇴근 버튼을 누르면 근태 시트에 자동으로 출퇴근 시간이 적히도록 엑셀 매크로 작성

![](attachments/Pasted%20image%2020240815040614.png)

## 파일명 변경 엑셀 만들기

- 폴더 내 파일명을 일괄 변경해주는 엑셀 매크로 만들기

![](attachments/Pasted%20image%2020240815035928.png)

## ChatGPT를 엑셀에서 사용할 수 있도록 커스텀 함수 만들기

- `GPT()` 함수 만들기

![](attachments/Pasted%20image%2020240815042447.png)

# 감사합니다