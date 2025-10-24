---
title: Git 및 Github 사용법
author: 배문형
type: module
---

## Git 설치

- Windows

```powershell
winget install -e Git.Git
```

- Mac

```bash
brew install git
```


### Git 설정

- 커밋에 기록될 이메일, 이름 설정

```bash
git config --global user.name "이름"
git config --global user.email "email@company.com"
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

- 풀 (땡겨오기)

```bash
git pull
```

***

- 브랜치 생성

```
git branch {branchName}
```

- 해당 브랜치로 변경 (체크아웃)

```bash
git checkout {branchName}
```

```bash
git checkout -b {branchName}
```

- 브랜치 병합

```bash
git merge {branchName}
```




