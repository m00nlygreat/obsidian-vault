### rust, perl 등 설치

```bash
sudo apt update && sudo apt install -y build-essential curl git perl pkg-config autoconf bison rustc cargo \
libssl-dev zlib1g-dev libreadline-dev libyaml-dev libffi-dev libgdbm-dev libdb-dev \
libncurses5-dev libncursesw5-dev uuid-dev ca-certificates
```

```bash
mise plugins update && rm -rf ~/.cache/mise/ruby ~/.cache/mise/ruby-build
```

- 공식 문서를 한 번 더 참고하자. 저렇게 많이 설치할 필요는 없다.

### ruby 설치

```bash
mise install ruby@3.4.2
```