## 압축하기

### 상대경로로 파일 이름이 적힌 list.txt 만들기

```
AppData\Local\Kakao\KakaoTalk\pref.ini
AppData\Local\Kakao\KakaoTalk\users\01b55173c6a37708cb3f1a9e0dd9ef2d579b2add\user_pref.ini
AppData\Local\Kakao\KakaoTalk\users\01b55173c6a37708cb3f1a9e0dd9ef2d579b2add\lab_pref.ini
```

### 명령어 쓰기

```cmd
"C:\Program Files\7-Zip\7z.exe" a -r compressed.7z @list.txt
```

## 실행파일 만들기
 
- `7zr`(경량 무설치)로는 안되고 `7z`로만 가능
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

- 다음 명령어 실행
	- `7z.sfx`, `config.txt`, `*.7z` 파일이 모두 cwd 에 있다고 가정
	- cmd 로 실행해야됨. powershell, wt 안됨

```
copy /b 7z.sfx + config.txt + files.7z my_installer.exe
```

- 실패했음 ㅋㅋ

