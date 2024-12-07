---
title: Make와 백엔드 자동화
author:
	- 배문형
---

# API

![API](../Topics/API.md)

# Make

## Make.com

- 구 인티그로맷(Integromat)
- 재피어(Zapier), IFTTT, n8n과 같은 **백엔드 자동화 도구**

### 재피어와의 비교

- 강력함: 보다 뛰어난 자유도
- 경제적: 넉넉한 무료 티어, 유료 기능도 재피어에 비해 저렴
- 인터페이스: 섬세한 시각화 및 노드식 UI 구성으로 직관적

![](attachments/make-intro.png)

## Terms

- 시나리오(Scenarios): 하나 하나의 작업을 지칭.
	- 모듈(Modules): 시나리오를 구성하는 하나 하나의 작업
	- 수행(Operations): 시나리오 실행 시 실행된 모듈 한 개당 1 Operation으로 과금 기준이 된다.
- 연결(Connections): 각 모듈의 실행을 위한 연결된 외부 서비스들의 인증/연결 내용들
- 웹훅(Webhooks): 외부에서 시나리오를 실행시킬 수 있는 API

## 시나리오(Scenarios)

### 시나리오를 시작시키는 3가지 방법

- Run Once를 눌러 직접 실행하기
- 스케줄을 통해 