# シェル環境について

サブシェル関係とバックグラウンドは実行したシェルとは別で実行される

`echo $BASHPID; (echo $BASHPID); cat <(echo $BASHPID); echo $(echo $BASHPID); { echo $BASHPID; }; echo $BASHPID &`

```plain
2055 # current shell
2385 # subshell
2386 # process substitution
2388 # command substitution
2055 # block
[1] 2389 # background
```
