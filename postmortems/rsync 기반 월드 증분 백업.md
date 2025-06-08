일단 

```bash
rsync -av world/ ../backup
```

rsync는 강력하고 쉬움

`--delete` : 원본 폴더에 없는 파일을 백업 대상 폴더에서 삭제함
`--link-dest [경로]`: 