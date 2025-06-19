- SSL 적용을 위해 nginx 필요함
- n8n은 소켓 통신을 사용해서 연결유지하므로 소켓 통신을 위한 설정 필요

```
```

- `/etc/nginx/sites-available/n8n`
	- 디렉토리 아니고 파일임. 없으면 생성

```bash
sudo vi /etc/nginx/sites-available/n8n
```


