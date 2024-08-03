# ヒストリー展開(!系)

command|desc
-|-
!^|最初の引数
!$|最後の引数
!:x|x番目の引数
!-n:x-y|x番目からy番目の引数
!-n|n回前のコマンド実行
!-n:x|n回前のコマンドのx番目の引数

## 検証

```bash
#!/bin/bash

mkdir history_test
cd !$ # cd history_test -> 直近のコマンド、最後の引数
rm -f "test"
touch "test-begin" "test-mid" "test-last"
echo "pre end"

rm !-2:2 # rm "test-mid" -> 2つ前のコマンド,2つ目の引数
echo !-4^ # echo -f -> 4つ前のコマンド,最初の引数
```

## コマンド実行履歴

`history`

## 実行したコマンドを.bash_historyに即時反映する

`export PROMPT_COMMAND='history -a; history -r'`
