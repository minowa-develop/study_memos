# ncコマンドと/dev/tcpでレスポンス出力有無の違いについて

## nc 192.0.2.1 80 < request_header

レスポンスが出力される

## cat request_header > /dev/tcp/192.0.2.1/80

一方向的にデータを送るだけで、レスポンスを処理しないため、レスポンスが出力されない

この方法でレスポンスを出力するには、レスポンスをソケットから取得する処理を追加しないといけない

```bash
#!/bin/bash

exec 3<>/dev/tcp/192.0.2.1/80
cat request_header >&3
cat <&3
exec 3>&-
```
