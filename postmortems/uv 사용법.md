### uv 시작

```bash
uv init
```

### uv sync

```bash
uv sync
```

`uv run`이 알아서 sync 하기 때문에 필요는 없다

### python interactive

```bash
uv run python
```

### 코드 실행

```bash
uv run {path}
```

### 패키지

설치

```bash
uv add {package-name}
```

제거

```bash
uv remove {package-name}
```

### pip

```bash
uv pip install {package-name}
```

`pyproject.toml` / `uv.lock` 에 기록하지 않고 설치