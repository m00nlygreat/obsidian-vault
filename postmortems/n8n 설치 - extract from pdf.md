- GCP Free tier 인스턴스에 n8n 설치하고
	- 별도 인증서 등 없이 cloudflare 가변(Flexible) SSL 적용
	- SSL 적용을 위해 `nginx` 필요함
- n8n은 소켓 통신을 사용해서 연결유지하므로 소켓 통신을 위한 설정 필요

- `/etc/nginx/sites-available/n8n`
	- 디렉토리 아니고 파일임. 없으면 생성 👇

```bash
sudo vi /etc/nginx/sites-available/n8n
```

### nginx 설정

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

- Extract from PDF 노드 사용 시 1.98 버전(25.6.19 현재 최신)에서 `pdfjs` 업데이트로 인한 `DOMMatrix is not defined` 오류 발생
- 따라서 작동하는 것이 확인된 1.93 으로 내려오니 여기서는 Code 노드를 사용해 다수의 binary를 여러개 item으로 분할(이메일 attachments를 반복하기 위한 경우 등..) 한 경우 다음 오류 발생
	- ERROR: The first argument must be of type string or an instance of Buffer, ArrayBuffer, or Array or an Array-like Object.
		- 최신버전에서도 나는 오류인지는 확인 안됨
	- 이 오류는 binary data 저장을 메모리가 아닌 파일 시스템으로 바꿔주고 파일을 읽을 수 있도록 허용해주면 됨. 아래 설정 참고 👇

#### docker-compose.yml 설정

```yaml
services:
  n8n:
    image: docker.n8n.io/n8nio/n8n:1.93.0
    container_name: n8n
    ports:
      - "5678:5678"
    volumes:
      - n8n_data:/home/node/.n8n
    environment:
      - WEBHOOK_URL=https://n8n.sites.address/
      - N8N_DEFAULT_BINARY_DATA_MODE=filesystem
      - N8N_BLOCK_FILE_ACCESS_TO_N8N_FILES=false
    restart: unless-stopped
volumes:
  n8n_data:
```