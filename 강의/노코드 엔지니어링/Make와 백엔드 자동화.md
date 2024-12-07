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
	- 모듈(Modules): 시나리오를 구성하는 하나 하나의 작업.
		- 트리거(Triggers): 모듈 중 시나리오를 시작하는 조건이 되는 모듈
	- 수행(Operations): 시나리오 실행 시 실행된 모듈 한 개당 1 Operation으로 과금 기준이 된다.
- 연결(Connections): 각 모듈의 실행을 위한 연결된 외부 서비스들의 인증/연결 내용들
- 웹훅(Webhooks): 외부에서 시나리오를 실행시킬 수 있는 API

## 시나리오(Scenarios)

### 시나리오를 시작시키는 3가지 방법

- Run Once를 눌러 직접 실행하기
- 스케줄을 통해 자동 실행하기
	- 트리거(Trigger)가 필요함
- 웹훅을 사용해 외부에서 실행하기
	- 이 경우 HTTP Response를 통해 결과값을 반환할 수 있다

### 트리거(Trigger)

- 모든 시나리오는 트리거로 실행이 되어야 한다. 
	- 대표적으로 'Watch ..' 로 시작하는 모듈
	- `ACID` 가 붙어있는 모듈들
- 시나리오에는 하나의 트리거만 존재할 수 있다

