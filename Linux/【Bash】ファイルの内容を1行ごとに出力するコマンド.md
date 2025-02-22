# ファイルの内容を1行ごとに出力するコマンドについて

## 模範解答

```bash
#!/bin/bash

while read -r line; do
  echo "${line}"
done <<< $'aaa\nbbb'
```

## Process

1. whileコマンドで標準入力された`aaa\nbbb`を受け取って改行で区切る
1. 区切った文字列`aaa`,`bbb`を`read -r line`に標準入力をとして渡す、`read -r line <<< "aaa"`
1. readコマンドで標準入力を変数lineに格納する
