---
title: Git 및 Github 사용법
author: 배문형
type: module
---

## Git 설치

```powershell
winget install -e Git.Git
```

## Git 명령어

- 리포지토리 클론

```bash
git clone https://github.com/... [dirName]
```

- 커밋 / 푸쉬

```bash
git status
```

```bash
git add .
```

```bash
git commit -m "커밋 메시지"
```

***

- 풀 (땡겨오기)

```bash
git pull
```

- 브랜치 생성

```
git branch {branchName}
```

- 해당 브랜치로 변경 (체크아웃)

```bash
git checkout {branchName}
```

