## sites-available to sites-enabled

- `sites-available`에 사용할 서버 모아놓고, `ln -s` 명령어 등을 사용해 `sites-enabled`에 링크해서 nginx 불러옴

## nginx 재시작

```bash
sudo systemctl reload nginx
```

## server block

```
server {
    listen 80;
    server_name lists.name;  # 또는 _;

    location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```