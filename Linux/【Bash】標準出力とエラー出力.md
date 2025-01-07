# 標準出力とエラー出力および、マージについて

## ファイル・ディスクリプターについて

プログラムがアクセスするファイルや標準入出力などをOSが識別するために用いる識別子

番号|出力先
-|-
0|標準入力(テーマには該当しない)
1|標準出力
2|エラー出力

## 記載方法と結果

記載方法|console出力|ファイル出力|用途
-|-|-|-
`コマンド > ファイル`|err|std|標準出力をファイルに出力
`コマンド >&2 ファイル`|err+std|std|consoleにすべて出力したい
`コマンド 2> ファイル`|std|err|ファイルにエラーを出力したい
`コマンド > ファイル 2>&1`|-|err+std|エラーを標準として扱い、ファイルに出力したい
`コマンド > ファイル >&2`|err+std|-|意味なし

## 実用について

特に、`コマンド > /dev/null 2>$1`で標準とエラーの両方をconsoleに出力しない用途で使用される

## 検証の事前準備

echo_str.sh

```bash
#!/bin/bash

echo "default echo"
echo "standard echo" >&1
echo "error echo" >&2
```

## 検証_ファイルの左側

実行コマンド(`>`の箇所はテスト方法に依存)

```bash
./echo_str.sh > /tmp/test.txt; echo "---file---"; cat /tmp/test.txt
```

### 通常(>)

```plain
error echo
---file---
default echo
standard echo
```

### 2>

```plain
default echo
standard echo
---file---
error echo
```

### 2>&1

```plain
default echo
standard echo
error echo
---file---
default echo
standard echo
```

### 1>&2

```plain
default echo
standard echo

error echo
---file---
default echo
standard echo
```

### ここまで

- `echo "hoge"`と`echo "hoge" >&1`は同じ
- `1>&2`と`2>&1`は同じ結果
  - 結局は2つのものをマージしているため同じになった?
- マージすると標準出力にはすべて出力され、fileには標準のみ出力される
- マージしてもfileに書き込む内容は標準のみで変わらない

## 検証_ファイルの右側

実行コマンド(`${kensyou}`の箇所はテスト方法に依存)

```bash
./echo_str.sh > /tmp/test.txt ${kensyou}; echo "---file---"; cat /tmp/test.txt
```

### 指定なし

```plain
error echo
---file---
default echo
standard echo
```

### 2>&1

```plain
---file---
default echo
standard echo
error echo
```

### 1>&2

```plain
default echo
standard echo
error echo
---file---
```

### ここまで

- `./echo_str.sh ${A} /tmp/test.txt ${B};`
  - Aはマージ(標準+エラー)してconsole出力する
  - Bは切り替えて(エラーを標準に移動or標準をエラーに移動)fileに出力する