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

        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }
}
```

- cloud-flare 가변 모드 사용시 이정도로 충분
- 맨 아래 두 줄은 wss (websocket over https를 위해서임)

## client_max_body_size

```
server {
    client_max_body_size 100M;
    # ...
}
```

위와같이 설정해서 업로드 제한을 풀어줄 수 있다