---
title: "Builder.io 개발자가 Claude Code를 사용하는 방법 (+ best tips)"
source: "https://news.hada.io/topic?id=22034"
author:
  - "[[spilist2]]"
published: 2025-07-17
created: 2025-07-17
description: "예전에는 Cursor 파워 유저였고 How I use Cursor (+ my best tips)라는 글로 인기를 끌었던 Builder.io의 Steve Swell이 이번에는 좋은 클로드 코드 팁 글을 올려줬길래 번역 + 요약해서 공유드립니다. (블로그 글에는 참고 영상과 코드 스니펫이 있습니다)IDE에서 통합해서 써라. 다만 나는 이제 커서는 CMD+K 자"
tags:
---
[▲](https://news.hada.io/)

(stdy.blog)

3 P by [spilist2](https://news.hada.io/user?id=spilist2) 4시간전 | [★ favorite](https://news.hada.io/) | [댓글과 토론](https://news.hada.io/topic?id=22034)

예전에는 Cursor 파워 유저였고 [How I use Cursor (+ my best tips)](https://www.builder.io/blog/cursor-tips) 라는 글로 인기를 끌었던 [Builder.io](https://www.builder.io/) 의 Steve Swell이 이번에는 좋은 클로드 코드 팁 글을 올려줬길래 번역 + 요약해서 공유드립니다. (블로그 글에는 참고 영상과 코드 스니펫이 있습니다)

- IDE에서 통합해서 써라. 다만 나는 이제 커서는 `CMD+K` 자동완성과 탭 자동완성에만 쓴다. 커서의 에이전트 모드는 클로드 코드 안될 때만 쓴다.
- 예전에는 코드 에디터 창 크기가 더 크고 에이전트는 사이드에 있었다. 요즘은 클로드 코드의 창 크기가 더 크다.
- Builder.io에는 18,000줄짜리 단일 React 컴포넌트가 있다. 이걸 제대로 다룬 AI가 아무것도 없었는데 클로드 코드는 해낸다.
- $100 플랜이고 보통 Opus만 쓴다. 보통 사람들은 기본 설정(50%는 Opus, 다쓰면 Sonnet)을 쓰는 걸로도 충분할 것이다. 제대로 쓰려면 새 작업 시작하기 전에는 항상 `/clear` 해라.
- 클로드 코드에게 권한 주는 플래그(`claude --dangerously-skip-permissions`)는 생각보다 위험하지 않아서 리스크 감수하고 써볼만 하다.
- 깃헙 통합(`/install-github-app`)으로 PR 리뷰해주는 거 의외로 쓸만하다. 로직 에러와 보안 이슈도 잘 찾아준다. 근데 기본 리뷰 프롬프트는 별로고, `claude-code-review.yml` 에서 수정해라.
- `#` 으로 메모리 빠르게 넣는 것도 좋다. 알아서 가장 적절한 메모리 파일에 넣어준다.
- 큐 시스템 좋다. 작업하고 있을 때 빼먹었던 거 그냥 하나씩 추가해두면 알아서 잘 해준다. 중간에 피드백 필요하면 그냥 무지성으로 수정하는 대신 나에게 되묻는 것도 좋다.
- 커스텀 훅, 슬래시 커맨드, 프로젝트별 설정 제대로 할수록 더 편해지는데 클로드 코드에게 요청하면 다 해준다.
- 커스텀 커맨드에 `$ARGUMENTS` 넣을 수 있는 것도 좋다. 서브폴더도 된다. `/buider/plugin` 입력하면 builder 폴더의 `plugin.md` 를 찾아간다.
- [Builder.io 익스텐션](https://www.builder.io/c/docs/projects-vscode) 을 IDE에 추가하면 클로드 코드처럼 동작하는 챗 인터페이스 + 디자인 프리뷰 + 비주얼 에딧도 가능하다. 클로드 코드 리버스 엔지니어링해서 최대한 비슷하게 인터페이스 만들었다.
- 그 외 처음 쓰는 사람이 모를 만한 것들
	- Shift + Enter로 새 줄 안 생기는데 `/terminal-setup` 하면 해결된다. (역자 주: 저는 Ctrl + J 씁니다)
	- IDE에 통합해놨을 때 파일 그냥 드래그하면 참조가 안 된다. (그렇게 하면 IDE에서 그냥 그 파일이 열린다) Shift 누른 채로 드래그해라.
	- 클로드를 멈추려면 CTRL+C가 아니라 Esc해야 한다.
	- 클립보드 이미지는 (Mac에서도) CMD+V가 아니라 CTRL+V 해야 들어간다.
	- 위 화살표 누르면 (세션 끝났어도) 이전 챗으로 갈 수 있다. Esc 두 번 누르면 모든 메시지 볼 수 있다.