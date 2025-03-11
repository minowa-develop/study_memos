# 名前付きパイプ

別プロセスにデータを受け渡しできるfifoファイルを作成

```bash
#!/bin/bash

mkfifo my_pipe
echo current $BASHPID
echo "Hello, Named Pipe!" > my_pipe &
(echo subproc: $BASHPID; cat < my_pipe)
```
