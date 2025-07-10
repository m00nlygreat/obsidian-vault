---
title: 캘린더 일정관리 GPTs 만들기
type: tutorial
author: 배문형
---

## 따라하기: 캘린더 일정관리 GPTs 만들기

Make의 웹훅을 사용하면, GPTs가 판단하에 Make의 시나리오를 실행시키게 할 수 있습니다. 이를 사용해, GPTs에게 우리의 구글 캘린더에 일정을 알아서 등록하게 하는 기능을 만들어 줘봅니다.

### Phase

전체 공정은 아래와 같습니다.

1. Make에서 새 웹훅 모듈을 만들고 대기하기
2. 새 GPTs를 만들고 작업(Actions) 만들기
3. [ActionsGPT](https://chatgpt.com/g/g-TYEliDU6A-actionsgpt)를 사용해서 **OpenAPI 스키마** 작성하기
4. Make에서 구글 캘린더