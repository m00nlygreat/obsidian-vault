- GCP Free tier 인스턴스에 n8n 설치하고 
	- cloudflare 가변 SSL 적용을 사용
	- SSL 적용을 위해 `nginx` 필요함
- n8n은 소켓 통신을 사용해서 연결유지하므로 소켓 통신을 위한 설정 필요

- `/etc/nginx/sites-available/n8n`
	- 디렉토리 아니고 파일임. 없으면 생성 👇

```bash
sudo vi /etc/nginx/sites-available/n8n
```

```nginx
server {
    listen 80;
    server_name n8n.sites.adress;

    location / {
        proxy_pass http://localhost:5678;
        proxy_http_version 1.1;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }
}
```

### extract from pdf 관련

- 1.98 버전에서 `pdfjs` 업데이트로 인한 DOMMatrix 오류 발생 
