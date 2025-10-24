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

### Windows

```powershell
winget install -e OpenJS.NodeJS
```

#### `winget`이 없는 경우

```powershell
$progressPreference = 'silentlyContinue'
Write-Host "Installing WinGet PowerShell module from PSGallery..."
Install-PackageProvider -Name NuGet -Force | Out-Null
Install-Module -Name Microsoft.WinGet.Client -Force -Repository PSGallery | Out-Null
Write-Host "Using Repair-WinGetPackageManager cmdlet to bootstrap WinGet..."
Repair-WinGetPackageManager -AllUsers
Write-Host "Done."
```

***

### Mac

```bash
brew install node
```

#### Homebrew가 없는 경우

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 설치하기

### Codex-CLI

```bash
npm install -g @openai/codex
```

#### 실행

```bash
codex
```

### Gemini-CLI (무료)

```bash
npm install -g @google/gemini-cli
```

#### 실행

```bash
gemini
```

## MCP 사용하기

### Codex

```bash
codex mcp add <server-name> --env VAR1=VALUE1 --env VAR2=VALUE2 -- <stdio server-command>
```

### GEMINI

- `.GEMINI/settings.json` 에 기록

```json
{ 
  "mcpServers": {
    "serverName": {
      "command": "path/to/server",
      "args": ["--arg1", "value1"],
      "env": {
        "API_KEY": "$MY_API_TOKEN"
      },
      "cwd": "./server-directory",
      "timeout": 30000,
      "trust": false
    }
  }
}
```

## MCP 서버 마켓

- [MCP.so](https://mcp.so)
- [Awesome MCP Servers](https://mcpservers.org)

### 추천 MCP 서버들

- Figma: 피그마 디자인을 읽어와 그대로 구현
- Taskmaster: 작업을 태스크로 쪼개고 
- Serena: LSP 서버를 사용해 사용하는 토큰을 줄여주고 작업속도 향상
- Supabase MCP