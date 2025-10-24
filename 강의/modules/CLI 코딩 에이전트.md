---
title: CLI 코딩 에이전트
author: 배문형
type: module
---

## CLI 코딩 에이전트 사용하기

- 터미널과 IDE에 통합되어 사용할 수 있는 CLI 코딩 에이전트 사용하기
- Codex CLI, Gemini Cli, Cluade-code 등
- MCP, 로컬 파일 시스템 접근, 명령어 실행 등 좀 더 코드를 직접적으로 조작하여 프로그래밍을 수행할 수 있음

## 필요한 것

- 터미널 사용법
	- `cd`, `dir`/`ls`, `exit`
- Git 사용법 및 Github 연동
	- `git init`, `git clone`, `git commit`, `git push`, `.gitignore`
- CLI 코딩 에이전트 설치 및 사용법
	- `node`, `npm`
- MCP, `AGENTS.md` 등 도구별 설정

![터미널 사용하기](터미널%20사용하기.md)

![Git 및 Github 사용법.md](Git%20및%20Github%20사용법.md)

## Node.js 설치

- Windows

```powershell
winget install -e OpenJS.NodeJS
```

- `winget`이 없는 경우

```powershell
$progressPreference = 'silentlyContinue'
Write-Host "Installing WinGet PowerShell module from PSGallery..."
Install-PackageProvider -Name NuGet -Force | Out-Null
Install-Module -Name Microsoft.WinGet.Client -Force -Repository PSGallery | Out-Null
Write-Host "Using Repair-WinGetPackageManager cmdlet to bootstrap WinGet..."
Repair-WinGetPackageManager -AllUsers
Write-Host "Done."
```