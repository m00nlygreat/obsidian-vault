```Powershell
Set-ItemProperty 'HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem' -Name 'LongPathsEnabled' -Value 1
```

- 설치하기 전에 Long Path 관련 설정

```
winget install LGUG2Z.komorebi
winget install LGUG2Z.whkd
```

- komorebi를 포터블처럼 (재설치 시 별도 설정 하지 않고 바로 실행)하려면 두 가지 env에 경로가 있어야 한다
	- `KOMOREBI_CONFIG_HOME`
	- `KOMOREBI_AHK_EXE`
- 본래 `USERPROFILE`을 사용하지만, config home을 설정함으로써 해당 폴더의 설정을 사용하도록 함.
- AutoHotkeyV2가 Win 키 리매핑을 위해 필요함. 