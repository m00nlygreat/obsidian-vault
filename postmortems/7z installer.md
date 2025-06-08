## 압축하기

### 상대경로로 파일 이름이 적힌 list.txt 만들기

### 명령어 쓰기

7z a compressed.7z @list.txt

## 실행파일 만들기
 
- 7zr로는 안되고 7z로만 가능
- 우선 `config.txt` 를 만들자

```
;!@Install@!UTF-8!
Title="My Installer"
BeginPrompt="압축을 시작합니다."
RunProgram="run.bat"
ExtractPathText="압축을 풀 폴더를 선택하세요."
InstallPath="C:\\MyApp"       ; ← 여기 지정 가능!
;!@InstallEnd@!
```

- 