# シンボリックリンクとハードリンクについて

リンク種類|参照先|参照方法|FS依存
-|-|-|-
シンボリックリンク|ファイルのパス|ファイルのパス|依存しない
ハードリンク|データの実体|参照パス|依存する

## FSへの依存について

- シンボリックリンクはinodeを参照せずファイルパスで参照するためFSに依存していない
- ハードリンクはリンク先のinodeを参照するためFSへの依存がある

※ ここでの異なるFSの定義は、同じxfsだとしても実態が異なれば異なるFSとみなす

## 検証

```bash
#!/bin/bash

echo test > test.txt
ln test.txt hard.ln
ln -s test.txt sinbol.ln
stat *.ln test.txt  -c"%n %i"
```

結果

```plain
test.txt 16778686
hard.ln 16778686
sinbol.ln 16779136
```
